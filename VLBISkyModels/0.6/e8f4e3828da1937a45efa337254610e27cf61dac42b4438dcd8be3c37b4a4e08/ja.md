```julia
struct ParabolicSegment{T} <: VLBISkyModels.GeometricModel{T}
```

画像領域内の無限に薄い放物線セグメント。セグメントはゼロを中心に、根は±1で、y切片は1です。

`T`が構築時に指定されていない場合、デフォルトで`Float64`になります。
