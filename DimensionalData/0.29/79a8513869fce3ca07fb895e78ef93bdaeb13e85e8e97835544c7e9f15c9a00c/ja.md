```
DimSelectors <: AbstractArray

DimSelectors(x; selectors, atol...)
DimSelectors(dims::Tuple; selectors, atol...)
DimSelectors(dims::Dimension; selectors, atol...)
```

[`DimIndices`](@ref)と同様ですが、選択された[`Selector`](@ref)を保持する`Dimensions`を返します。

別の`AbstractDimArray`に`DimSelectors`でインデックスを付けることは、補間を行うのと似ています。

## キーワード

  * `selectors`: `Near`、`At`、または`Contains`、またはこれらの混合タプル。`At`がデフォルトで、正確な値または`atol`内の値のみが使用されます。
  * `atol`: `At`セレクタのみに使用される`atol`値。個々の`At`セレクタ内で`atol`が設定されている場合は無視されます。

## 例

ここでは、`DimSelectors`を使用して`Near`で別の`DimArray`のルックアップに`DimArray`を補間できます。これは本質的に最近傍補間と同等です。

```jldoctest; setup = :(using DimensionalData, Random; Random.seed!(123))
julia> A = rand(X(1.0:3.0:30.0), Y(1.0:5.0:30.0), Ti(1:2));

julia> target = rand(X(1.0:10.0:30.0), Y(1.0:10.0:30.0));

julia> A[DimSelectors(target; selectors=Near), Ti=2]
┌ 3×3 DimArray{Float64, 2} ┐
├──────────────────────────┴──────────────────────────────────────── dims ┐
  ↓ X Sampled{Float64} [1.0, 10.0, 22.0] ForwardOrdered Irregular Points,
  → Y Sampled{Float64} [1.0, 11.0, 21.0] ForwardOrdered Irregular Points
└─────────────────────────────────────────────────────────────────────────┘
  ↓ →  1.0        11.0       21.0
  1.0  0.691162    0.218579   0.539076
 10.0  0.0303789   0.420756   0.485687
 22.0  0.0967863   0.864856   0.870485
```

`At`を使用すると、正確な補間のみを使用することが保証され、一方で`Contains`を使用して`Intervals`をサンプリングすると、各値がルックアップに存在する区間からのみ取得されることが保証されます。
