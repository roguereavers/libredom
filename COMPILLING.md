Compiling Freedoom
==================

This document is a general overview of Freedoom’s dependencies
required to build it.  See `README` for a description of what Freedoom
_is_, and `BUILD-SYSTEM` for the technical details on _how_ Freedoom
is built.

Required software
-----------------

Building the Freedoom IWADs pretty much simply requires the following:

  * _make_: While there is some attempt to keep our Makefiles
    portable, testing does not really happen on anything but
    https://www.gnu.org/software/make/[GNU Make] (patches to fix
    portability are most welcome!).  On non-GNU systems, it might be
    available in a package and binary named as _gmake_.
  * _Python_: Freedoom uses several Python programs in its tree to
    assist with building the IWADs.  Python 3.x is required, we no
    longer support Python 2.
  * _Pillow_: A Python image manipulation module that provides the
    features we need for scaling and composing various graphics of the
    game.
  * _DeuTex_ 5.0: Freedoom depends on features developed in this
    version of DeuTex and will not build on earlier versions.  It is
    available at https://github.com/Doom-Utils/deutex in source and
    Windows binary formats.

All or most of this software should already be available in your
operating system’s software repository, with the likely exception of
DeuTex, which is easy to build.

Building Freedoom
-----------------

Significant work has been put into making this step easy.  At the top
of the Freedoom source tree, you should be able to simply type `make`
and wait for it to eventually produce the IWAD files in the `wads`
sub-directory.  Parallel make builds are safe too, such as with `make
-j`.

If only interested in a specific IWAD, you can also run `make
wads/freedm.wad`, `make wads/freedoom1.wad`, `make wads/freedoom2.wad`.

As mentioned in the prior section, the Makefile only recieves testing
with the GNU version of Make.  If the primary version of your Make is
not GNU and it fails, try `gmake` instead.

Building on Microsoft Windows
-----------------------------

Freedoom has normally seen all of its development on Unix systems,
nevertheless some people like to compile Freedoom on Windows.  This is
possible, although complicated by our choice of tooling for the
project.

GNU environments for Windows such as https://cygwin.com/[Cygwin],
http://www.msys2.org/[MSYS2], or
https://blogs.msdn.microsoft.com/wsl/[WSL] provide sufficient shell
capabilities to build Freedoom.  The dependencies listed previously
for Freedoom apply just as well to a Windows environment.

Instructions on how to use a GNU system and shell are out of scope of
this document.

Optional software
-----------------

  * _Git_: Freedoom is developed using the Git version control system,
    the latest developments can be tracked with it.
  * _AsciiDoc_: The `*.adoc` files are all written in AsciiDoc markup,
    and it can be used to generate HTML versions of all these
    documents.  This is used as part of the `make dist` and `make
    install` targets, to generate the `NEWS.html` and `README.html`
    files for inclusion with official Zip files.  Different
    implementations (eg, AsciiDoctor) may be selected by passing
    `ASCIIDOC` and `ASCIIDOC_MAN` environment variables to `make`.
  * _AsciiDoctor PDF_: Our manual, maintained in `manual/manual.adoc`,
    has a hard dependency on this implementation of AsciiDoc for its
    superior-looking PDF output.
  * _Zip_: The `make dist` target uses Zip to create release archives
    for FreeDM, Phase 1, and Phase 2.  This can also provide an easy
    way to automate generating in-development versions for other
    people.
