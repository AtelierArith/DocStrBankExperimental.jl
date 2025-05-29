```
read_libsvm(filepath::String; has_query=false)
read_libsvm(raw::Vector{UInt8}; has_query=false)
```

Read data in the LIBSVM format from either a file or a raw byte vector and return it as a tuple containing feature matrix, target labels, and optionally query entries.

# Arguments

  * `filepath::String`: The path to a file containing data in LIBSVM format. Only one of `filepath` or `raw` should be provided.
  * `raw::Vector{UInt8}`: A vector of raw bytes containing data in LIBSVM format. Only one of `filepath` or `raw` should be provided.
  * `has_query::Bool=false`: A boolean flag indicating whether the data includes query entries.

# Returns

  * A tuple `(x, y)` if `has_query` is `false`, where

      * `x::Matrix{Float64}`: The feature matrix as a dense `Float64` matrix, where each row represents a data point, and each column represents a feature.
      * `y::Vector{Float64}`: The target labels as a dense vector of `Float64`.
  * A tuple `(x, y, q)` if `has_query` is `true`, where

      * `x::Matrix{Float64}`: The feature matrix as a dense `Float64` matrix.
      * `y::Vector{Float64}`: The target labels as a dense vector of `Float64`.
      * `q::Vector{Int}`: The query entries as a dense vector of `Int`.
