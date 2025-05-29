```julia
Mesh2D(dx, dy)
```

二次元の正規背景メッシュ

# 引数:

  * `dx::Float64`:  x次元の変形
  * `dy::Float64`:  y次元の変形

# 戻り値:

  * 二次元メッシュオブジェクト

# 例:

```jldoctest
# 2Dメッシュを生成
mesh = Mesh2D(1.0, 0.5);

# 検証
println(mesh)

# 出力

2d mesh:
    dx: 1.0
    dy: 0.5
```
