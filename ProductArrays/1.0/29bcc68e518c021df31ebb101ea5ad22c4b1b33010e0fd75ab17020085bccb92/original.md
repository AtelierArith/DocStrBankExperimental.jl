```
productArray(vectors...)
```

The output is a lazy form of

```julia
collect(Iterators.product(vectors...))
```

i.e. it is an AbstractArray in contrast to `Iterators.product(vectors...)`. So is accessible with `getindex` and gets default Array implementations for free. In particular it can be passed to `Base.PermutedDimsArray` for lazy permutation and `vec()` to obtain a lazy `Base.ReshapedArray`.

Examples:

```jldoctest
julia> A = productArray(1:3, (:a,:b))
3×2 ProductArrays.ProductArray{Tuple{UnitRange{Int64}, Tuple{Symbol, Symbol}}, Tuple{Int64, Symbol}, 2}:
 (1, :a)  (1, :b)
 (2, :a)  (2, :b)
 (3, :a)  (3, :b)

julia> vec(A)
6-element reshape(::ProductArrays.ProductArray{Tuple{UnitRange{Int64}, Tuple{Symbol, Symbol}}, Tuple{Int64, Symbol}, 2}, 6) with eltype Tuple{Int64, Symbol}:
 (1, :a)
 (2, :a)
 (3, :a)
 (1, :b)
 (2, :b)
 (3, :b)

julia> sizeof(A) == sizeof(1:3) + sizeof((:a,:b))
true

julia> A == collect(Iterators.product(1:3, (:a,:b)))
true
```
