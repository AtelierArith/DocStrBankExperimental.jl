```
IVFADCIndex(data [;kwargs])
```

Main constructor for building an inverse file system for billion-scale ANN search.

# Arguments

  * `Matrix{T<:AbstractFloat}` input data

# Keyword arguments

  * `kc::Int=DEFAULT_COARSE_K` number of clusters (Voronoi cells) to employ

in the coarse quantization step

  * `k::Int=DEFAULT_QUANTIZATION_K` number of residual quantization levels to use
  * `m::Int=DEFAULT_QUANTIZATION_M` number of residual quantizers to use
  * `coarse_quantizer::Symbol=DEFAULT_COARSE_QUANTIZER` coarse quantizer
  * `coarse_distance=DEFAULT_COARSE_DISTANCE` coarse quantization distance
  * `quantization_distance=DEFAULT_QUANTIZATION_DISTANCE` residual quantization distance
  * `quantization_method=DEFAULT_QUANTIZATION_METHOD` residual quantization method
  * `coarse_maxiter=DEFAULT_COARSE_MAXITER` number of clustering iterations for obtaining

the coarse vectors

  * `quantization_maxiter=DEFAULT_QUANTIZATION_MAXITER` number of clustering iterations for

residual quantization

  * `index_type=UInt32` type for the indexes of the vectors in the inverted list
