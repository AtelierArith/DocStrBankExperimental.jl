```
sample(::Type{T<:Real}=Int, A::AbstractArray, n_sim::Int; [dims=:], [n_cat=nothing])
```

Draw `n_sim` samples from the distribution which corresponds to the sum of the independent categorical distributions defined by the probability mass vector(s), `A`, storing the result in an array of `eltype` `T` of sufficient size and dimension as determined by the input, `A`, the number of categories, `n_cat`, and the (potential) reduction dimensions, `dims`.

`dims` is an optional keyword argument used to specify an in-place sum on the indices of `A` (if `A` is an array of arrays). `n_cat` may be optionally specified, or inferred from the available data; validity indices will be checked regardless.

In the simplest case, `A` may be a single probability mass vector, for which compatible types are `AbstractVector{<:Real}`, `SparseVector{<:Real, <:Integer}`, and `AbstractVector{Tuple{<:Integer, <:Real}}`, the last of which is simply another representation of a sparse vector.

In the second case, `A` may be an `AbstractArray{V, N} where {V, N}` in which `V` is any of the types specified above for a single probability mass vector. That is, an array of vectors.

In the third case, `A` may be an `AbstractArray{W, M} where {W<:AbstractArray{V, N}, M} where {V, N}` in which `W` is any of the types specified in the second case. In other words, an array of arrays of vectors.

See also: [`tsample`](@ref), [`vsample`](@ref), [`vtsample`](@ref)
