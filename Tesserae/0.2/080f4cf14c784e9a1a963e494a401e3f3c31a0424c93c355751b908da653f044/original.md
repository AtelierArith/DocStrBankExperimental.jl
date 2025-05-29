```
WLS(kernel)
```

`WLS` performs a local weighted least squares fit for the `kernel`. This results in the same kernel used in moving least squares MPM[^MLSMPM]. `kernel` is one of [`BSpline`](@ref) and [`uGIMP`](@ref).

[^MLSMPM]: [Hu, Y., Fang, Y., Ge, Z., Qu, Z., Zhu, Y., Pradhana, A. and Jiang, C., 2018. A moving least squares material point method with displacement discontinuity and two-way rigid body coupling. ACM Transactions on Graphics (TOG), 37(4), pp.1-14.](https://doi.org/10.1145/3197517.3201293)
