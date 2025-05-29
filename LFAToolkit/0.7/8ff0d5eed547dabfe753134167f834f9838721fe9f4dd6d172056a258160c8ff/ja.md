```julia
Mesh3D(dx, dy, dz)
```

三次元の正規背景メッシュ

# 引数:

  * `dx::Float64`:  x次元の変形
  * `dy::Float64`:  y次元の変形
  * `dz::Float64`:  z次元の変形

# 戻り値:

  * 三次元メッシュオブジェクト

# 例:

```jldoctest
# 3Dメッシュを生成
mesh = Mesh3D(1.0, 0.5, 0.3);

# 検証
println(mesh)

# 出力

3d mesh:
    dx: 1.0
    dy: 0.5
    dz: 0.3
```
