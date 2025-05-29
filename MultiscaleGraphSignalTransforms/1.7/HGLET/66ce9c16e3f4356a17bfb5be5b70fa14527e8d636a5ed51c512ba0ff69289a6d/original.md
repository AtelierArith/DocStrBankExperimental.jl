function HGLET_Synthesis(dvec::Vector{Float64}, GP::GraphPart, BS::BasisSpec,                          G::GraphSig; gltype::Symbol = :L)

### Input Arguments

  * `dvec`: the expansion coefficients corresponding to the chosen basis
  * `GP`: a GraphPart object
  * `BS`: a BasisSpec object
  * `G`: a GraphSig object
  * `gltype`: :L, :Lrw, or :Lsym, indicating which eigenvectors are used

### Output Argument

  * `f`: the reconstructed signal
  * `GS`: the reconstructed GraphSig object
