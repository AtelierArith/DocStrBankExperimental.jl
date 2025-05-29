```
constraint_node_directionality(
    wm::AbstractWaterModel,
    i::Int;
    nw::Int=nw_id_default
)
```

方向に基づく制約を追加するための制約テンプレート（[`constraint_sink_directionality`](@ref)、[`constraint_source_directionality`](@ref)、または[`constraint_intermediate_directionality`](@ref)）を適切な場合に使用します。ここで、`wm`はWaterModelsオブジェクト、`i`は制約が追加されるノードのインデックス（該当する場合）、`nw`はサブネットワーク（または時間）インデックスです。
