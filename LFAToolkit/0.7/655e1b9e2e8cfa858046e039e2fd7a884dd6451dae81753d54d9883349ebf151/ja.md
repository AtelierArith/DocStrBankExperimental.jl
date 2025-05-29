```julia
IdentityPC()
```

スムーザーなしでマルチグリッドを調査するための単位前処理器

# 戻り値:

  * 単位前処理器オブジェクト

# 例:

```jldoctest
# セットアップ
mesh = Mesh2D(1.0, 1.0);
mass = GalleryOperator("mass", 4, 4, mesh);

# 前処理器
identity = IdentityPC(mass);

# 検証
println(identity)

# 出力

単位前処理器
```
