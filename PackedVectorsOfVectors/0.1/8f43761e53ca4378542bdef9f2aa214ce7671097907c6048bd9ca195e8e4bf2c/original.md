```
allocate_packed(T, init, n) -> PackedVectorOfVectors
```

Allocate a packed vector of vectors with nested element type `T` such that the `k`th nested vector has length `nth(n,k)`. See the documentation of `Vector{T}(init,n)` regarding the meaning of `init`.

# Examples

```jldoctest
julia> allocate_packed(Ref{Int}, undef, [1,2,3])
3-element pack(::Vector{Vector{Ref{Int64}}}):
 [#undef]
 [#undef, #undef]
 [#undef, #undef, #undef]
```
