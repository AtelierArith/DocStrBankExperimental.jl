```
(levlistfull, levlengthsfull, transfull) = bsfull(GP::GraphPart, BS::BasisSpec, trans::Vector{Bool})
```

Given a BasisSpec object, return the full-length, redundant levlist, levlengths, and trans descriptions.

### Input Arguments

  * `GP::GraphPart`: an input GraphPart object
  * `BS::BasisSpec`: an input BasisSpec object
  * `trans::Vector{Bool}`: a specification of the transforms used for the HGLET-GHWT hybrid transform (default: null)
  * `levlengthsp::Bool`: a flag to return levlengthsfull (default: false)
  * `transp::Bool`: a flag to return transfull (default: false)

### Output Arguments

  * `levlistfull::Vector{UInt8}`: the full-length, redundant levels list description
  * `levlengthsfull::Vector{UInt8}`: the full-length, redundant levels lengths description
  * `transfull::Matrix{Bool}`: the full-length, redundant trans description
