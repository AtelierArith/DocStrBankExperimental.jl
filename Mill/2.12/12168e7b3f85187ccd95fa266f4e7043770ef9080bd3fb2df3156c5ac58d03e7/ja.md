```
BagModel(im, a, bm=identity)
```

引数から[`BagModel`](@ref)を構築します。`im`は[`AbstractMillModel`](@ref)、`a`は[`AbstractAggregation`](@ref)または[`BagCount`](@ref)、`bm`は[`ArrayModel`](@ref)である必要があります。

モデルノードの代わりに任意の関数を`im`として渡すことも可能です。その場合、[`ArrayNode`](@ref)にラップされます。

# 例

```jldoctest
julia> m = BagModel(ArrayModel(Dense(3, 2)), SegmentedMeanMax(2), Dense(4, 2))
BagModel ↦ [SegmentedMean(2); SegmentedMax(2)] ↦ Dense(4 => 2)  4 arrays, 14 params, 224 bytes
  ╰── ArrayModel(Dense(3 => 2))  2 arrays, 8 params, 120 bytes

julia> m = BagModel(Dense(4, 3), BagCount(SegmentedMean(3)))
BagModel ↦ BagCount(SegmentedMean(3)) ↦ identity  1 arrays, 3 params (all zero), 52 bytes
  ╰── ArrayModel(Dense(4 => 3))  2 arrays, 15 params, 148 bytes
```

関連項目: [`AbstractMillModel`](@ref)、[`AbstractAggregation`](@ref)、[`BagCount`](@ref)、[`AbstractBagNode`](@ref)、[`BagNode`](@ref)、[`WeightedBagNode`](@ref)。
