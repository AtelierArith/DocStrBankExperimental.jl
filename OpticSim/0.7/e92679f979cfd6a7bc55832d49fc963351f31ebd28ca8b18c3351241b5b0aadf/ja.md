```
Ray{T,N} <: AbstractRay{T,N}
```

純粋に幾何学的な光線で、`origin + alpha * direction`として定義されます。

```julia
Ray(origin::SVector{N,T}, direction::SVector{N,T})
```

次のアクセサメソッドがあります：

```julia
direction(ray::Ray{T,N}) -> SVector{N,T}
origin(ray::Ray{T,N}) -> SVector{N,T}
```
