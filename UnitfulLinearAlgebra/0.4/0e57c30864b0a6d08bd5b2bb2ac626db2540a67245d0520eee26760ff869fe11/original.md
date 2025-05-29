```
struct UnitfulMatrix
```

Extend `DimArray` to use dimensions for units, also add `exact` boolean flag

struct UnitfulMatrix{T,N,D<:Tuple,A<:AbstractArray{T,N}} <: AbstractUnitfulVecOrMat{T,N,D,A}     data::A     dims::D     exact::Bool end
