```
f = ghwt_synthesis(dvec::Matrix{Float64}, GP::GraphPart, BS::BasisSpec)
```

Given a vector of GHWT expansion coefficients and info about the graph partitioning and the choice of basis, reconstruct the signal

### Input Arguments

  * `dvec::Matrix{Float64}`: the expansion coefficients corresponding to the chosen basis
  * `GP::GraphPart`: an input GraphPart object
  * `BS::BasisSpec`: an input  BasisSpec object

### Output Arguments

  * `f::Matrix{Float64}`: the reconstructed signal(s)
