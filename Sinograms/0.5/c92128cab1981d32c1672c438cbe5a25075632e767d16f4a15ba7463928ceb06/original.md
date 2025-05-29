```
parker_weight(rg::CtFan; T::Type{<:AbstractFloat} = Float32, kwargs...)
```

For 3D case, return `Array{T,3}` where size is

  * `(1,1,1)` typical fan case with 360° orbit
  * `(ns,1,na)` atypical fan case including short scan
