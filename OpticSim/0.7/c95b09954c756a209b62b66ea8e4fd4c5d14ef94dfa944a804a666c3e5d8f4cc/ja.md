```
BSplineSurface{P,S,N,M} <: SplineSurface{P,S,N,M}
```

曲線の次数はu方向とv方向で同じであり、すべてのスパンで固定されています。uおよびvのノットベクトルは異なることが許可されています - *両方を同じにするように変更するかもしれません*。

u方向の制御点は列に対応し、uの最小値は行1に対応します。v方向の制御点は行に対応し、vの最小値は列1に対応します。

!!! danger
    このサーフェスは有効な半空間を作成せず、正しく機能するためには更新が必要です。


```julia
BSplineSurface{P,S,N,M}(knots::KnotVector{S}, controlpoints::AbstractArray{<:AbstractArray{S,1},2})
BSplineSurface{P,S,N,M}(uknots::KnotVector{S}, vknots::KnotVector{S}, controlpoints::AbstractArray{<:AbstractArray{S,1},2})
```
