```
QXTensor(indices::Array{<:Index, 1},
         hyper_indices::Array{<:Array{Int64, 1}, 1},
         storage::Union{Nothing, <: NDTensors.TensorStorage}=nothing)
```

QXTensorコンストラクタは、指定されたインデックスとハイパーインデックスを持つ新しいQXTensorのインスタンスを作成します。ストレージデータ構造が指定されていない場合、その形状のMockTensorがストレージとして追加されます。
