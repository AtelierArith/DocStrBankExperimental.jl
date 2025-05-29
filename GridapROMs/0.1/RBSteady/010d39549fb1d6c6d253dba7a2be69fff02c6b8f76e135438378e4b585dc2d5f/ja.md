```
galerkin_projection(a::Projection,b::Projection) -> ReducedProjection
galerkin_projection(a::Projection,b::Projection,c::Projection,args...) -> ReducedProjection
```

(Petrov) 射影マップ `b` を部分空間 `a`（行射影）に、必要に応じて部分空間 `c`（列射影）にガレルキン射影します。
