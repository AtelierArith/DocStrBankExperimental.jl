Construct a `CiteLibrary`.

```julia
library(collections; libname, liburn, license, cexversion)

```

## Optional parameters

  * `liburn` Unique identifier for this library. Must be a subtype of `Urn`.
  * `libname` Name of library (value returned by `label`)
  * `license` License. Default is cc-nc-by.
  * `cexversion` Version of the CEX standard used in serializing library. Default is the current version.
