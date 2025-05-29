```
Ellipse{T} <: Surface{T}
```

楕円面は、有効なCSGオブジェクトではありません。矩形の法線に対する回転は`rotationvec`によって定義されます。`rotationvec×surfacenormal`はu軸に沿ったベクトルとして取られます。

**[`AbstractOpticalSystem`](@ref)の検出器として使用できます。**

```julia
Ellipse(halfsizeu::T, halfsizev::T, [surfacenormal::SVector{3,T}, centrepoint::SVector{3,T}]; interface::NullOrFresnel{T} = nullinterface(T))
```

最小のケースは、`surfacenormal = [0, 0, 1]`の原点に中心を持つ楕円を返します。
