```
ChainedVector(arrays::Vector{<:AbstractVector})
```

Create a `ChainedVector` of a `Vector` of homogenously-typed `AbstractVector`. The "chain" of input vectors will be treated as a single, long vector. A full set of typical mutable operations are supported (e.g. `push!`, `append!`, etc.).

As implementation details, mutable operations on single elements (e.g. `setindex!`, `push!`) operate in-place or mutate an existing chained array, while `append!`/`prepend!` are optimized to "chain" the incoming array to the existing chained arrays.
