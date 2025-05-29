```
basevec(::Type{Vec{dim, T}})
basevec(::Type{Vec{dim, T}}, i)
basevec(::Vec{dim, T})
basevec(::Vec{dim, T}, i)
```

次元 `dim` と型 `T` に対応する基底ベクトルのタプルを返します。オプションの整数 `i` を使用して i:番目の基底ベクトルを抽出することができます。エイリアス `eᵢ` も使用でき、`e\_i<TAB>` と書かれます。

# 例

```jldoctest
julia> eᵢ(Vec{2, Float64})
([1.0, 0.0], [0.0, 1.0])

julia> eᵢ(Vec{2, Float64}, 2)
2-element Vec{2, Float64}:
 0.0
 1.0
```
