```
rotate!(p::Pattern3D, α::Float64, β::Float64, γ::Float64)
```

3Dパターンをオイラー角α、β、γ（ラジアン単位）で回転させます。ZYZ規約を使用します。

# 引数

  * `p::Pattern3D`: 回転させるパターン
  * `α::Float64`: 最初の回転角（Z軸周り）
  * `β::Float64`: 2番目の回転角（Y'軸周り）
  * `γ::Float64`: 3番目の回転角（Z''軸周り）

# 例

```julia
nmer = Nmer3D()
rotate!(nmer, π/4, π/6, π/3)
```
