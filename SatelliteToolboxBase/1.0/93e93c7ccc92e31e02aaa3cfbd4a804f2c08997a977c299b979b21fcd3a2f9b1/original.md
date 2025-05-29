```
Ellipsoid(a::T1, f::T2) where {T1 <: Number, T2 <: Number}
```

Construct an ellipsoid (see [`Ellipsoid`](@ref)) with semi-major axis `a` and flattening `f`. The other elements in the structure are computed automatically.

The ellipsoid type is obtained by promoting `T1` and `T2` and converting to `float`.
