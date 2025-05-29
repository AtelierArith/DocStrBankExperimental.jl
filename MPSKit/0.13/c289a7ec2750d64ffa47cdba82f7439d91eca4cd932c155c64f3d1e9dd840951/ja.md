```julia
struct WII <: MPSKit.Algorithm
```

MPOの演算子指数のオイラー近似の一般化。

## フィールド

  * `tol::Float64`: 収束基準の許容誤差
  * `maxiter::Int64`: 最大反復回数

## 参考文献

  * [Zaletel et al. Phys. Rev. B 91 (2015)](@cite zaletel2015)
  * [Paeckel et al. Ann. of Phys. 411 (2019)](@cite paeckel2019)
