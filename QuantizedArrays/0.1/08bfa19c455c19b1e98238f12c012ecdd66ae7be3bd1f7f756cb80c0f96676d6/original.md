```
quantize(aa; [;kwargs])
```

Quantize an array `aa`.

# Arguments

  * `aa::AbstractArray` input array to be quantized

# Keyword arguments

  * `k::Int` the number of vector prototypes in each codebook
  * `m::Int` the number of codebooks
  * `method::Symbol` the algorithm to be employed for codebook

generation; possible values are `:sample` (default), `:pq` for classical k-means clustering codebooks and `:opq` for 'cartesian' k-means clustering codebooks

  * `distance::PreMetric` the distance to be used in the

codebook generation methods and data encoding

Other codebook generation algorithm specific keyword arguments such as `maxiter::Int` can be specified as well.
