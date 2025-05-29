```
InfiniteTimeReachability{R <: Real, VT <: Vector{<:CartesianIndex}}
```

`InfiniteTimeReachability`は[`FiniteTimeReachability`](@ref)に似ていますが、時間の範囲が無限である、すなわち$H = \infty$です。実際には、値関数が収束するまで値反復を行うことを意味し、これはいくつかの閾値`convergence_eps`によって定義されます。収束の閾値は、最新のベルマン残差の最大値が`convergence_eps`未満であることです。
