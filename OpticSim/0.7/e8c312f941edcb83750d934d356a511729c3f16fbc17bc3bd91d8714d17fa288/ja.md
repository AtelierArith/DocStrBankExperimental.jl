```
SphericalCap{T} <: ParametricSurface{T}
```

球面キャップ表面は、実質的に無限平面から球を引き算した半空間を作成します。視覚化されるのは球面キャップ自体のみで、平面は含まれません。正の法線側は表面の外側です。

**[`AbstractOpticalSystem`](@ref)の検出器として使用できます。**

```julia
SphericalCap(radius::T, ϕmax::T, [surfacenormal::SVector{3,T}, centrepoint::SVector{3,T}]; interface::NullOrFresnel{T} = nullinterface(T))
```

最小のケースでは、`surfacenormal = [0, 0, 1]`の原点に中心を持つ球面キャップが返されます。
