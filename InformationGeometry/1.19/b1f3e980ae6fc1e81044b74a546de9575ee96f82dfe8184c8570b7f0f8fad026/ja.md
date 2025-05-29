```
IntegrateND(F::Function,Cube::HyperCube; tol::Real=1e-12, WE::Bool=false, kwargs...)
```

関数 `F` を **HCubature.jl** を使用して `Cube` 上で `tol` の許容誤差で積分します。`WE=true` の場合、結果は `Measurement` として返され、結果の推定誤差も含まれます。
