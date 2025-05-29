```
Hexagon{T} <: Surface{T}
```

六角形の表面は、有効なCSGオブジェクトではありません。六角形の法線周りの回転は`rotationvec`によって定義されます。`rotationvec×surfacenormal`はu軸に沿ったベクトルとして取られます。

```julia
Hexagon(side_length::T, [surfacenormal::SVector{3,T}, centrepoint::SVector{3,T}]; rotationvec::SVector{3,T} = [0.0, 1.0, 0.0], interface::NullOrFresnel{T} = nullinterface(T))
```

最小のケースは、`surfacenormal = [0, 0, 1]`の原点に中心を持つ長方形を返します。
