```
rotate!(p::Pattern2D, θ::Float64)
```

2Dパターンを角度θ（ラジアン単位）だけ回転させます。

# 引数

  * `p::Pattern2D`: 回転させるパターン
  * `θ::Float64`: ラジアン単位の回転角

# 例

```julia
nmer = Nmer2D()
rotate!(nmer, π/4)  # 45度回転
```
