```
get_spatial_property(pos, property::AbstractArray, model::ABM)
```

連続エージェント位置を、[`ContinuousSpace`](@ref) 上の空間フィールドのいくつかの離散化を表す `property` の適切な `index` に変換します。次に、`property[index]` を返します。例えば、`property` をインプレースで変更するために `index` を直接取得するには、[`get_spatial_index`](@ref) を使用してください。
