```
Rectangle{T} <: Surface{T}
```

矩形の表面であり、有効なCSGオブジェクトではありません。矩形の法線周りの回転は`rotationvec`によって定義されます。`rotationvec×surfacenormal`はu軸に沿ったベクトルとして取られます。

**[`AbstractOpticalSystem`](@ref)の検出器として使用できます。**

```julia
Rectangle(halfsizeu::T, halfsizev::T, [surfacenormal::SVector{3,T}, centrepoint::SVector{3,T}]; rotationvec::SVector{3,T} = [0.0, 1.0, 0.0], interface::NullOrFresnel{T} = nullinterface(T))
```

最小のケースでは、`surfacenormal = [0, 0, 1]`の原点に中心を持つ矩形が返されます。
