```
data_lens(n, l)
```

モデルノードのレンズ `l` をデータノード `n` の同じ位置にアクセスするための新しいレンズに変換します。

# 例

```jldoctest
julia> n = ProductNode((BagNode(randn(Float32, 2, 2), bags([0:-1, 0:-1])), ArrayNode(Float32[1 2; 3 4])))
ProductNode  2 obs
  ├── BagNode  2 obs
  │     ╰── ArrayNode(2×2 Array with Float32 elements)  2 obs
  ╰── ArrayNode(2×2 Array with Float32 elements)  2 obs

julia> m = reflectinmodel(n)
ProductModel ↦ Dense(20 => 10)  2 arrays, 210 params, 928 bytes
  ├── BagModel ↦ BagCount([SegmentedMean(10); SegmentedMax(10)]) ↦ Dense(21 => 10)  4 arrays, 240 params, 1.102 KiB
  │     ╰── ArrayModel(Dense(2 => 10))  2 arrays, 30 params, 208 bytes
  ╰── ArrayModel(Dense(2 => 10))  2 arrays, 30 params, 208 bytes

julia> data_lens(n, (@optic _.ms[2]))
(@o _.data[2])
```

関連情報: [`data_lens`](@ref).
