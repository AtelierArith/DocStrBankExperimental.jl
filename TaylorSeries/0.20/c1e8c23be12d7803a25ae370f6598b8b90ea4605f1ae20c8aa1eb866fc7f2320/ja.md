```
TaylorN([T::Type=Float64], nv::Int; [order::Int=get_order()])
```

`nv`-番目の独立した `TaylorN{T}` 変数を多項式として定義するためのショートカットです。順序はキーワードパラメータ `order` を通じて定義され、そのデフォルトは `get_order()` に対応します。`T` のデフォルトの型は `Float64` です。

```julia
julia> TaylorN(1)
 1.0 x₁ + 𝒪(‖x‖⁷)

julia> TaylorN(Rational{Int},2)
 1//1 x₂ + 𝒪(‖x‖⁷)
```
