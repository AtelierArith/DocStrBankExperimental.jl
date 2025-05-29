```julia
computesymbols(identity, ω, θ)
```

アイデンティティ前処理されたオペレーターのシンボル行列を計算または取得します

# 引数:

  * `identity::IdentityPC`:  シンボル行列を計算するためのアイデンティティ前処理器
  * `ω::Array`:              スムージング重み係数配列
  * `θ::Array`:              フーリエモード周波数配列（次元ごとに1つの周波数）

# 戻り値:

  * アイデンティティ前処理器 (I) のシンボル行列

# 例:

```jldoctest
using LinearAlgebra

# セットアップ
mesh = Mesh2D(1.0, 1.0);
mass = GalleryOperator("mass", 4, 4, mesh);

# 前処理器
identity = IdentityPC(mass);

# シンボルを計算
A = computesymbols(identity, [], []);

# 検証
@assert A ≈ I

# 出力

```
