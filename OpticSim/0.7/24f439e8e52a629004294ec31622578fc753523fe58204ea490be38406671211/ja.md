```
AcceleratedParametricSurface{T,N,S} <: ParametricSurface{T,N}
```

解析的交差が実現できない[`ParametricSurface`](@ref)のラッパークラス（例：[`ZernikeSurface`](@ref)、[`ChebyshevSurface`](@ref））。代わりにサーフェスは三角形分割され、正確な光線交差点を決定するために反復的（ニュートン・ラフソン）プロセスが実行されます。`S`はラップされるParametricSurfaceの型です。

```julia
AcceleratedParametricSurface(surf::ParametricSurface{T,N}, numsamples::Int = 17; interface::NullOrFresnel{T} = nullinterface(T))
```
