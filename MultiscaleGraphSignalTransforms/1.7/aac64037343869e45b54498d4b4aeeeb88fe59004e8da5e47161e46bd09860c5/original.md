```
(pm,v) = partition_fiedler(W; method, v)
```

Partition the vertices of a graph according to the Fiedler vector

### Input Arguments

  * `W::SparseMatrixCSC{Float64,Int}`: the edge weight matrix
  * `method::Symbol`: the parition method to be used (:L or :Lrw or else ...)
  * `v::Vector{Float64}`: the Fiedler vector supplied if `v` is a null vector

### Output Arguments

  * `pm::Vector{Int}`: a vector of 1's and -1's
  * `v::Vector{Float64}`: the Fiedler vector used for graph partitioning

Copyright 2015 The Regents of the University of California

Implemented by Jeff Irion (Adviser: Dr. Naoki Saito) Translated and revised by Naoki Saito, Feb. 9, 2017
