```
Taylor1([T::Type=Float64], order::Int)
```

与えられた `order` の `Taylor1{T}` 多項式の独立変数を定義するショートカット。`T` のデフォルト型は `Float64` です。

```julia
julia> Taylor1(16)
 1.0 t + 𝒪(t¹⁷)

julia> Taylor1(Rational{Int}, 4)
 1//1 t + 𝒪(t⁵)
```
