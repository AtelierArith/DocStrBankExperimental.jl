function dvec_Threshold(dvec::Array{Float64}, SORH::String, keep::Float64,                 GP::GraphPart, BS::BasisSpec)

Threshold HGLET / GHWT coefficients

### Input Arguments

  * `dvec::Array{Float64,2}`        the vector of expansion coefficients
  * `SORH::String`        use soft ('s') or hard ('h') thresholding
  * `keep::Float64`        a fraction between 0 and 1 which says how many coefficients should be kept
  * `GP::GraphPart`          a GraphPart object, used to identify scaling coefficients
  * `BS::BasisSpec`          a BasisSpec object, used to identify scaling coefficients

### Output Argument

  * `dvec_new::Vector{Float64}`        the thresholded expansion coefficients
  * `kept::Float64`        the number of coefficients kept
