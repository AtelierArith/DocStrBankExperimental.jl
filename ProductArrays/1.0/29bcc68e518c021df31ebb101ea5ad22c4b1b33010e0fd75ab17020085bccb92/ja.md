```
productArray(vectors...)
```

出力は、次の遅延形式です。

```julia
collect(Iterators.product(vectors...))
```

つまり、`Iterators.product(vectors...)`とは異なり、これはAbstractArrayです。したがって、`getindex`でアクセスでき、デフォルトのArray実装を無料で取得します。特に、遅延置換のために`Base.PermutedDimsArray`に渡すことができ、遅延`Base.ReshapedArray`を取得するために`vec()`を使用できます。

例:

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
