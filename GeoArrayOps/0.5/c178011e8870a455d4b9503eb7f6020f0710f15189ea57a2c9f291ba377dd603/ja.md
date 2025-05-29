```
curvature(dem::Matrix{<:Real}; cellsize=1.0)
```

曲率は[`slope`](@ref)の導関数であり、したがってDEMの二次導関数です。
