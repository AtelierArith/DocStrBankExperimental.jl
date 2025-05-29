```
KernelCorrection(kernel)
```

`KernelCorrection`[^KC] は、境界付近で安定したシミュレーションを実現するために `kernel` を修正します。修正されたカーネルは、単位の分割 $\sum_i w_{ip} = 1$ だけでなく、境界付近での線形場再現 $\sum_i w_{ip} \bm{x}_i = \bm{x}_p$ も満たします。実装では、これは単に境界付近で [`WLS`](@ref) を適用します。`kernel` は [`BSpline`](@ref) または [`uGIMP`](@ref) のいずれかです。さらに [`SteffenBSpline`](@ref) も参照してください。

[^KC]: [Nakamura, K., Matsumura, S., & Mizutani, T. (2023). Taylor particle-in-cell transfer and kernel correction for material point method. *Computer Methods in Applied Mechanics and Engineering*, 403, 115720.](https://doi.org/10.1016/j.cma.2022.115720)
