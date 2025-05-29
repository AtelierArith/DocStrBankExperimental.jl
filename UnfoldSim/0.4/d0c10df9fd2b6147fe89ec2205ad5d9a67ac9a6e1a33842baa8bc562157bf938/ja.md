```
orientation(hart::Hartmut; type = "cortical")
```

HArtMuTモデルの（皮質または人工的な）ソースの方向を返します。

方向ベクトルのノルムは1で、値は-1から1の間です。

# キーワード引数

  * `type = "cortical"`: "皮質"または"人工的"な方向を返すかどうかを定義します。

# 戻り値

  * `Matrix{Float64}`: 3D空間の方向。出力の次元は`sources x spatial dimensions`です。

# 例

```julia-repl
julia> h = Hartmut();
Please cite: HArtMuT: Harmening Nils, Klug Marius, Gramann Klaus and Miklody Daniel - 10.1088/1741-2552/aca8ce

julia> orientation(h)
2004×3 Matrix{Float64}:
 -0.921919   0.364292   0.131744
 -0.900757  -0.415843  -0.125345
 -0.954087   0.117479  -0.27553
 -0.814613  -0.55344    0.17352
 -0.790526   0.276849  -0.546281
  ⋮                    
 -0.962905   0.20498   -0.17549
 -0.828358   0.557468  -0.0552498
 -0.963785  -0.265607  -0.0239074
 -0.953909   0.203615   0.22045
 -0.75762    0.128027   0.640016
```
