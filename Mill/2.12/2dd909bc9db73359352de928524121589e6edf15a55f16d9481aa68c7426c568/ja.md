```
BagModel{T <: AbstractMillModel, A <: Union{AbstractAggregation, BagCount}, U}
    <: AbstractMillModel
```

[`AbstractBagNode`](@ref)を処理するためのモデルノードです。最初に、すべてのインスタンスに対して「インスタンス（サブ）モデル」`im`を適用し、次に要素ごとのセグメント集約`a`を行い、最後にデータノード内の各バッグの集約された表現に最終モデル`bm`を適用します。

# 例

```jldoctest; filter=r"\s*-?[0-9]+\.[0-9]+[\.]*\s*"
julia> Random.seed!(0);

julia> n = BagNode(ArrayNode(randn(Float32, 3, 2)), bags([0:-1, 1:2]))
BagNode  2 obs
  ╰── ArrayNode(3×2 Array with Float32 elements)  2 obs

julia> m = BagModel(ArrayModel(Dense(3, 2)), SegmentedMeanMax(2), Dense(4, 2))
BagModel ↦ [SegmentedMean(2); SegmentedMax(2)] ↦ Dense(4 => 2)  4 arrays, 14 params, 224 bytes
  ╰── ArrayModel(Dense(3 => 2))  2 arrays, 8 params, 120 bytes

julia> m(n)
2×2 Matrix{Float32}:
 0.0  1.05...
 0.0  0.49...

julia> m(n) == m.bm(m.a(m.im(n.data), n.bags))
true
```

参照: [`AbstractMillModel`](@ref), [`AbstractAggregation`](@ref), [`AbstractBagNode`](@ref),     [`BagNode`](@ref), [`WeightedBagNode`](@ref).
