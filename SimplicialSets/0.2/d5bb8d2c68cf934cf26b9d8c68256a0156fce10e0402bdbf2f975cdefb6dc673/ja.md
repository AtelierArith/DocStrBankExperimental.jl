```
ProductSimplex{T<:Tuple{Vararg{AbstractSimplex}}} <: AbstractSimplex

ProductSimplex{T}{t::Tuple{Vararg{AbstractSimplex}} [; dim::Integer]}

ProductSimplex(t::Tuple{Vararg{AbstractSimplex}} [; dim::Integer])
ProductSimplex(xs::AbstractSimplex... [; dim::Integer])
```

単体集合の積を表す型。空の積も許可されます。構成単体はすべて同じ次元でなければなりません。タプルとして、または個別の引数として与えることができます。

空の積の場合、結果の単体の次元を決定するためにキーワード引数 `dim` が必要です。それ以外の場合、`dim` はオプションですが、存在する場合は正しいものでなければなりません。

詳細は [`Tuple(x::ProductSimplex)`](@ref) を参照してください。

# 例

```jldoctest
julia> x, y = SymbolicSimplex(:x, 2), SymbolicSimplex(:y, 2)
(x[0,1,2], y[0,1,2])

julia> z = ProductSimplex(x, y)
(x[0,1,2],y[0,1,2])

julia> w = ProductSimplex(dim = 2)
()

julia> dim(w)
2

julia> ProductSimplex(x, y; dim = 1)
ERROR: dimensions of simplices do not match
[...]
```
