```
AdamCache(Y)
```

`Y`の第一および第二モーメントを保存します（ゼロで初期化）。

第一および第二モーメントは`B₁`および`B₂`と呼ばれます。

キャッシュが同次空間のインスタンス（例：[`StiefelManifold`](@ref) $St(n,N)$）で呼び出されると、モーメントは$\mathfrak{g}^\mathrm{hor}$の要素として初期化されます（[`StiefelLieAlgHorMatrix`](@ref)）。

# 例

```jldoctest
using GeometricMachineLearning

Y = rand(StiefelManifold, 5, 3)
AdamCache(Y).B₁

# 出力

5×5 StiefelLieAlgHorMatrix{Float64, SkewSymMatrix{Float64, Vector{Float64}}, Matrix{Float64}}:
 0.0  -0.0  -0.0  -0.0  -0.0
 0.0   0.0  -0.0  -0.0  -0.0
 0.0   0.0   0.0  -0.0  -0.0
 0.0   0.0   0.0   0.0   0.0
 0.0   0.0   0.0   0.0   0.0
```
