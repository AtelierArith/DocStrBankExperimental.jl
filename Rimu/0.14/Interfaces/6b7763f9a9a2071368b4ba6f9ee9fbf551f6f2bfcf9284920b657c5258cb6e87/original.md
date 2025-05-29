```
compress!([::CompressionStrategy,] v) -> ::NTuple{N,::Symbol}, ::NTuple{N}
compress!([::CompressionStrategy,] w, v) -> ::NTuple{N,::Symbol}, ::NTuple{N}
```

Compress the vector `v`. The one-argument version compresses the vector in-place. The two-argument vector stores the result in `w`. The [`CompressionStrategy`](@ref) associated with the [`StochasticStyle`](@ref) of `v` is used to determine the type of compression.

Returns two tuples, containing the names and values of statistics that are to be reported.
