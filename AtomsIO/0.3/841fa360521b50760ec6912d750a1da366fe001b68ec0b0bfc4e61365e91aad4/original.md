Parse or write file using [XCrySDenStructureFormat](https://github.com/azadoks/XCrySDenStructureFormat.jl).

Supported formats:

  * [XSF](http://www.xcrysden.org/doc/XSF.html) and [AXSF](http://www.xcrysden.org/doc/XSF.html) atomic structure files. These are the files typically used by the [XCrySDen](http://www.xcrysden.org/) visualisation program.

!!! note "Format has been dropped in AtomsIO 0.3"
    This file format has been supported in earlier versions of AtomsIO, but is now dropped as the implementing packages lack a maintainer and no longer function with the most recent version of AtomsBase. In case of interest, see the [draft PR](https://github.com/azadoks/XCrySDenStructureFormat.jl/pull/6), which can be completed to re-enable support.

