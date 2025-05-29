```
WLS(kernel)
```

`WLS`は`kernel`のための局所加重最小二乗フィットを実行します。これにより、移動最小二乗MPM[^MLSMPM]で使用されるのと同じカーネルが得られます。`kernel`は[`BSpline`](@ref)および[`uGIMP`](@ref)のいずれかです。

[^MLSMPM]: [Hu, Y., Fang, Y., Ge, Z., Qu, Z., Zhu, Y., Pradhana, A. and Jiang, C., 2018. A moving least squares material point method with displacement discontinuity and two-way rigid body coupling. ACM Transactions on Graphics (TOG), 37(4), pp.1-14.](https://doi.org/10.1145/3197517.3201293)
