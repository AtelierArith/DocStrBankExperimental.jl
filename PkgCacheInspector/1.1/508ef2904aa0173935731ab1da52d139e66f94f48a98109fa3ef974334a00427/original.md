```julia
struct PkgCacheSizes
```

Stores the sizes of different "sections" of the pkgimage. The main section is the package image itself. However, reconstructing a pkgimage for use requires auxillary data, like the addresses of internal pointers that need to be modified to account for the actual base address into which the pkgimage was loaded. Each form of auxillary data gets stored in distinct sections.

  * `sysdata`: Size of the image. This is the portion of the file that gets returns by `info_cachefile`.

  * `isbitsdata`: Size of the `const` internal data section (storing things not visible from Julia, like datatype layouts).

  * `symboldata`: Size of the symbol section, for Symbols stored in the image.

  * `tagslist`: Size of the GC tags section, holding references to objects that require special re-initialization for GC.

  * `reloclist`: Size of the relocation-list section, holding references to within-image pointers that need to be offset by the actual base pointer upon reloading.

  * `gvarlist`: Size of the "gvar" (global variable) list of LLVM-encoded objects.

  * `fptrlist`: Size of the function-pointer list, referencing native code.
