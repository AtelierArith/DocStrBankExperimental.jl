(dvec, BS) = ghwt*tf*bestbasis(dmatrix::Array{Float64,3}, GP::GraphPart; cfspec::Float64 = 1.0, flatten::Any = 1.0)

Implementation of time-frequency adapted GHWT method = eGHWT. Modified from the algorithm in the paper: "A Fast Algorithm for Adapted Time Frequency Tilings" by Christoph M. Thiele and Lars F. Villemoes.

### Input Arguments

  * `dmatrix::Array{Float64,3}`: the matrix of expansion coefficients
  * `GP::GraphPart`: an input GraphPart object
  * `cfspec::Any`: the specification of cost functional to be used (default: 1.0, i.e., 1-norm)
  * `flatten::Any`: the method for flattening vector-valued data to scalar-valued data (default: 1.0, i.e., 1-norm)

### Output Arguments

  * `dvec::Matrix{Float64}`: the vector of expansion coefficients corresponding to the eGHWT best basis
  * `BS::BasisSpec`: a BasisSpec object which specifies the eGHWT best basis

Copyright 2018 The Regents of the University of California

Implemented by Yiqun Shao (Adviser: Dr. Naoki Saito)
