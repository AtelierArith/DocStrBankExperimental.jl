```
function initlogiset(
    dataset::AbstractDimensionalDataset,
    features::AbstractVector;
    worldtype_by_dim::Union{Nothing,AbstractDict{Int,Type{<:AbstractWorld}}}=nothing
)::UniformFullDimensionalLogiset
```

与えられた [`AbstractDimensionalDataset`](@ref) に基づいて、[`UniformFullDimensionalLogiset`](@ref) を構築します。

# キーワード引数

  * worldtype*by*dim::Union{Nothing,AbstractDict{Int,Type{<:AbstractWorld}}}=nothing:

整数としての次元性と関連する [`AbstractWorld`](@ref) 型とのマッピング; 指定されていない場合、これは `0 => OneWorld, 1 => Interval, 2 => Interval2D` にデフォルト設定されます。

さらに [`AbstractDimensionalDataset`](@ref)、SoleLogics.AbstractWorld、MultiData.dimensionality、[`UniformFullDimensionalLogiset`](@ref) を参照してください。
