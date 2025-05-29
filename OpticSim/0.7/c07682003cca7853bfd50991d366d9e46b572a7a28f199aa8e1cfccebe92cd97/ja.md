```
Intersection{T,N} <: IntervalPoint{T}
```

[`Ray`](@ref)が[`Surface`](@ref)に当たる点を表します。これは、レイに沿った距離、ワールド空間における交差点、ワールド空間における法線、表面上のUV、および[`OpticalInterface`](@ref)のヒットで構成されています。

以下のアクセサメソッドがあります：

```julia
point(a::Intersection{T,N}) -> SVector{N,T}
normal(a::Intersection{T,N}) -> SVector{N,T}
uv(a::Intersection{T,N}) -> SVector{2,T}
u(a::Intersection{T,N}) -> T
v(a::Intersection{T,N}) -> T
α(a::Intersection{T,N}) -> T
interface(a::Intersection{T,N}) -> OpticalInterface{T}
flippednormal(a::Intersection{T,N}) -> Bool
```
