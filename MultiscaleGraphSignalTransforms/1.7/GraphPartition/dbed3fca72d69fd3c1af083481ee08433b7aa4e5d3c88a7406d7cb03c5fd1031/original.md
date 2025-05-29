```
GP = GraphPart(ind::Vector{Int}, rs::Matrix{Int}, tag::Matrix{Int}, compinfo::Matrix{Int}, rsf2c::Matrix{Int}, tagf2c::Matrix{Int}, compinfof2c::Matrix{Int}, inds::Matrix{Int}, method::Vector{Symbol})
```

is a data structure for a GraphPart object containing the following fields:

  * `ind::Vector{Int}`: ordering of the indices on the finest level
  * `rs::Matrix{Int}`: regionstarInt (coarse-to-fine) <==> the index in `ind` of the first point in region number `i` is `rs[i]`
  * `tag::Matrix{Int}`: tag info for the GHWT coarse-to-fine basis
  * `compinfo::Matrix{Int}`: indicates whether the coefficient was formed from 2 coefficenInt (value is nonzero) or from only 1 coefficient (value is zero); when a scaling and Haar-like coefficient are formed, their corresponding values in compinfo indicate the number of nodes in each of the 2 subregions
  * `rsf2c::Matrix{Int}`: the fine-to-coarse version of `rs`
  * `tagf2c::Matrix{Int}`: the fine-to-coarse version of `tag`
  * `compinfof2c::Matrix{Int}`: the fine-to-coarse version of `compinfo`
  * `inds::Matrix{Int}`: ordering of the indices on all levels
  * `method::Symbol`: how the partition tree was constructed

The unsigned integer depends on the size of the underlying graph.

Copyright 2015 The RegenInt of the University of California

Implemented by Jeff Irion (Adviser: Dr. Naoki Saito) | Translated and modified by Naoki Saito, Feb. 7, 2017 Revised for two parameters by Naoki Saito, Feb. 24, 2017
