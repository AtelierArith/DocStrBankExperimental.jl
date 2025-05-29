```
membership(regions_list::Vector{Region}, p::Union{Vector{Float64},Vector{Int64}})
```

ハイパーサーフェス配置の補集合の領域のリストと点 p を入力します。出力は点 p が属する領域です。

オプション:

  * `reltol = 1e-6`, `abstol = 1e-9`: ODE ソルバーの精度のためのパラメータです。

```
