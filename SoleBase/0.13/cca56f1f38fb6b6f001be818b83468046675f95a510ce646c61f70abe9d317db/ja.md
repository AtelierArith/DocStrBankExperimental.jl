```
slicedataset(
    dataset::D,
    dataset_slice::AbstractVector{<:Integer};
    allow_no_instances = false,
    return_view = false,
    kwargs...,
) where {D<:AbstractDataset}
```

インスタンスのサブセットを持つ機械学習データセットを返します。

# 実装

カスタムデータセット表現でslicedatasetを使用するには、次のメソッドを提供します。

```
instances(
    dataset::D,
    dataset_slice::AbstractVector{<:Integer},
    return_view::Union{Val{true},Val{false}};
    kwargs...
) where {D<:AbstractDataset}
```

[`concatdatasets`](@ref)を参照してください。
