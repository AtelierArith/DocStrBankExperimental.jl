```
(x,z)=get_degopt_crefs(k)
(x,z)=get_degopt_crefs(graph)
```

線形結合参照（crefs）を[`graph_degopt`](@ref)に関連して返します。具体的には、`x`は`Vector{Tuple{Vector{Tuple{Symbol,Int}},Vector{Tuple{Symbol,Int}}}}`であり、`x[2][1]`は乗算の左辺の係数に対応します。

```
B2=(α_2_1 *I + α_2_2 *A)(β_2_1 *I + β_2_2 *A)
```

すなわち、`[α_2_1, α_2_2]`に対応するcrefsです。[`graph_degopt`](@ref)を参照してください。したがって、`get_coeffs(graph,x[2][1])`は係数の対応する数値を返します。
