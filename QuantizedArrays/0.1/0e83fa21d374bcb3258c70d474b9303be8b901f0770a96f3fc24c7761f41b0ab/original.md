```
build_codebooks(X, k, m, U [;method=DEFAULT_METHOD, distance=DEFAULT_DISTANCE, kwargs])
```

Generates `m` codebooks of `k` prototypes each for the input matrix `X` using the algorithm specified my `method` and distance `distance`. Specific codebook aglorithm keyword arguments can be specified as well.

# Arguments

  * `X::AbstractMatrix{T}` input matrix of type `T`
  * `k::Int` number of prototypes/codebook
  * `m::Int` number of codebooks
  * `U::Type{<:Unsigned}` type for codebook codes

# Keyword arguments

  * `method::Symbol` the algorithm to be employed for codebook

generation; possible values are `:sample` (default), `:pq` for classical k-means clustering codebooks and `:opq` for 'cartesian' k-means clustering codebooks

  * `distance::PreMetric` the distance to be used in the

codebook generation methods and data encoding

  * `kwargs...` other codebook generation algorithm specific

keyword arguments such as `maxiter::Int`.
