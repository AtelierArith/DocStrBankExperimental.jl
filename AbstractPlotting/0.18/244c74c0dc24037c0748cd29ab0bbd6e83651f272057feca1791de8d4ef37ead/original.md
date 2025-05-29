```
convert_arguments(SL::SurfaceLike, x::VecOrMat, y::VecOrMat, z::Matrix)
```

If `SL` is `Heatmap` and `x` and `y` are vectors, infer from length of `x` and `y` whether they represent edges or centers of the heatmap bins. If they are centers, convert to edges. Convert eltypes to `Float32` and return outputs as a `Tuple`.
