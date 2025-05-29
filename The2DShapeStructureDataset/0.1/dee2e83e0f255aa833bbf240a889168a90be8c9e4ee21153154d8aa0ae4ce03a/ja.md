```
shape_sample_inner(name, n)
```

指定された名前の形状の内部から均等にサンプリングされた `n` 点の `2 ⨯ n` `HybridMatrix` を返します。

```julia
julia> shape_sample_inner("Bone-1", 10)
2×10 HybridArrays.HybridMatrix{2, StaticArraysCore.Dynamic(), Float64, 2, Matrix{Float64}} with indices SOneTo(2)×Base.OneTo(10):
 0.0915315  0.125075   0.751956  0.580064  0.780953  0.0356033  0.143631  0.0505262  0.337685  0.597154
 0.177619   0.0742084  0.907282  0.955151  0.828131  0.141015   0.138244  0.150312   0.466503  0.809213
```
