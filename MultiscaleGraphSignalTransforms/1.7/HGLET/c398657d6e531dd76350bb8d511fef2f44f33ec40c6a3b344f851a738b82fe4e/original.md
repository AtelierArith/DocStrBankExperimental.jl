function HGLET*GHWT*Synthesis(dvec::Matrix{Float64},GP::GraphPart,BS::BasisSpec,trans::Array{Bool,2},G::GraphSig)

```
Given a vector of HGLET & GHWT expansion coefficients, info about the
graph partitioning, and the choice of basis and corresponding transforms,
reconstruct the signal.
```

### Input Arguments

  * `dvec`:   the expansion coefficients corresponding to the chosen basis
  * `GP`:     a GraphPart object
  * `BS`:     a BasisSpec object
  * `trans`:  a specification of the transforms used for the HGLET-GHWT hybrid transform   00 = HGLET with L   01 = HGLET with Lrw   10 = HGLET with Lsym   11 = GHWT
  * `G`:      a GraphSig object

### Output Argument

  * `f`:      the reconstructed signal
  * `GS`:     the reconstructed GraphSig object
