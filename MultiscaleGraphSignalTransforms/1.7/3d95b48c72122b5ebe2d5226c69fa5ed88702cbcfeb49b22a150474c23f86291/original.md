```
function LPHGLET_Synthesis(dvec::Vector{Float64}, GP::GraphPart, BS::BasisSpec, G::GraphSig; gltype::Symbol = :L, ϵ::Float64 = 0.3)
```

Perform Lapped-HGLET Synthesis transform

### Input Arguments

  * `dvec`: the expansion coefficients corresponding to the chosen basis
  * `GP`: a GraphPart object
  * `BS`: a BasisSpec object
  * `G`: a GraphSig object
  * `gltype`: :L or :Lsym, indicating which eigenvectors are used
  * `ϵ`: relative action bandwidth (default: 0.3)

### Output Argument

  * `f`: the reconstructed signal
  * `GS`: the reconstructed GraphSig object
