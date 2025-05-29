```
function initlogiset(
    dataset::AbstractDimensionalDataset,
    features::AbstractVector;
    worldtype_by_dim::Union{Nothing,AbstractDict{<:Integer,<:Type}}=nothing
)::UniformFullDimensionalLogiset
```

与えられた[`AbstractDimensionalDataset`](@ref)に基づいて、[`UniformFullDimensionalLogiset`](@ref)を構築します。

# キーワード引数

  * worldtype*by*dim::Union{Nothing,AbstractDict{<:Integer,<:Type}}=nothing:

整数としての次元性と関連する[`AbstractWorld`](@ref)型とのマッピング; 指定されていない場合、デフォルトで`Dict(0 => OneWorld, 1 => Interval, 2 => Interval2D)`に設定されます。

他にも[`AbstractDimensionalDataset`](@ref)、SoleLogics.AbstractWorld、MultiData.dimensionality、[`UniformFullDimensionalLogiset`](@ref)を参照してください。
