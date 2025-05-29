```
shape_sample_outline(name, n)
```

指定された名前の形状のアウトラインから均等にサンプリングされた `n` ポイントの `2 ⨯ n` `HybridMatrix` を返します。

```julia
julia> shape_sample_outline("Bone-1", 10)
2×10 HybridArrays.HybridMatrix{2, StaticArraysCore.Dynamic(), Float64, 2, Matrix{Float64}} with indices SOneTo(2)×Base.OneTo(10):
 0.652387  0.476934  0.220565  0.358224  0.0707124  0.224358  0.446889  0.435535  0.538483  0.786873
 0.765361  0.708831  0.167959  0.369937  0.100747   0.144465  0.661627  0.643784  0.812571  0.894025
```
