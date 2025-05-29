```julia
Mesh1D(dx)
```

1次元の正規背景メッシュ

# 引数:

  * `dx::Float64`: x次元の変形

# 戻り値:

  * 1次元メッシュオブジェクト

# 例:

```jldoctest
# 1Dメッシュを生成
mesh = Mesh1D(1.0);

# 検証
println(mesh)

# 出力

1d mesh:
    dx: 1.0
```
