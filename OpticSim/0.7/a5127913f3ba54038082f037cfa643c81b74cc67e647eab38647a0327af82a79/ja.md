```
BezierSurface{P,S,N,M} <: SplineSurface{P,S,N,M}
```

制御点のグリッドによって定義されたベジェ曲面。

!!! danger
    この曲面は有効な半空間を作成せず、正しく機能するためには更新が必要です。


```julia
BezierSurface{P,S,N,M}(controlpoints::AbstractArray{<:AbstractArray{S,1},2})
```
