```
rotate!(p::Pattern3D, R::Matrix{Float64})
```

3Dパターンを回転行列Rで回転させます。

# 引数

  * `p::Pattern3D`: 回転させるパターン
  * `R::Matrix{Float64}`: 3x3回転行列

# 例

```julia
nmer = Nmer3D()
# z軸周りに90度の回転行列を作成
θ = π/2
R = [cos(θ) -sin(θ) 0; sin(θ) cos(θ) 0; 0 0 1]
rotate!(nmer, R)
```
