```
Lee <: Closure
```

リー閉包を実装します $b(r) = -\frac{\zeta\gamma^*(r)^2}{2} \left( 1- \frac{\phi \alpha \gamma^*(r)}{1 + \alpha\gamma^*(r)} \right) $。ここで $\gamma^* = \gamma + ρ f(r)/2$ であり、$ f(r)$ はメイヤーf関数、$\rho$ は密度です。さらに、$\zeta$、$\phi$、および $\alpha$ は熱力学的一貫性またはゼロ分離定理を用いて決定できる自由パラメータです。

例:

```julia
closure = Lee(1.073, 1.816, 1.0, 0.4) # ζ, ϕ, α, ρ
```

参考文献:

Lee, Lloyd L. "An accurate integral equation theory for hard spheres: Role of the zero‐separation theorems in the closure relation." The Journal of chemical physics 103.21 (1995): 9388-9396.
