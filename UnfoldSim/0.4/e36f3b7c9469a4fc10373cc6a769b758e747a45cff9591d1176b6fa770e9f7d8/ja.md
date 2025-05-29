```
magnitude(headmodel::AbstractHeadmodel)
```

与えられた `headmodel` のリードフィールド（および潜在的にソースの方向）に基づいて大きさを返します。

`headmodel` にソースの方向が含まれている場合、これらは計算に使用されます。そうでない場合、ソースの方向がすでに含まれていると仮定して `leadfield` が返されます。注意してください（少なくとも HArtMuT モデルの場合）、皮質ソースのリードフィールドが使用されます。

# 戻り値

  * `Matrix{Float64}`: ソースの方向を考慮して、各電極で測定されたポテンシャルへの各ソースの寄与。出力の次元は `electrodes x sources` です。

# 例

```julia-repl
# HArtMut モデルを例として使用
julia> h = Hartmut();
引用してください: HArtMuT: Harmening Nils, Klug Marius, Gramann Klaus and Miklody Daniel - 10.1088/1741-2552/aca8ce

julia> magnitude(h)
227×2004 Matrix{Float64}:
  0.111706   …   0.301065
  0.0774359      0.332934
  ⋮          ⋱  
 -0.164539      -0.246555
```
