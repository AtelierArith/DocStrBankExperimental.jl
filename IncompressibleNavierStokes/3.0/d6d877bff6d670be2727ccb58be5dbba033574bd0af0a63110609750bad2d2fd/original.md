```julia
get_scale_numbers(
    u,
    setup
) -> NamedTuple{(:uavg, :ϵ, :η, :λ, :Reλ, :L, :τ, :Re_int), <:NTuple{8, Any}}

```

Get the following dimensional scale numbers [Pope2000](@cite):

  * Velocity $u_\text{avg} = \langle u_i u_i \rangle^{1/2}$
  * Dissipation rate $\epsilon = 2 \nu \langle S_{ij} S_{ij} \rangle$
  * Kolmolgorov length scale $\eta = (\frac{\nu^3}{\epsilon})^{1/4}$
  * Taylor length scale $\lambda = (\frac{5 \nu}{\epsilon})^{1/2} u_\text{avg}$
  * Taylor-scale Reynolds number $Re_\lambda = \frac{\lambda u_\text{avg}}{\sqrt{3} \nu}$
  * Integral length scale $L = \frac{3 \pi}{2 u_\text{avg}^2} \int_0^\infty \frac{E(k)}{k} \, \mathrm{d} k$
  * Large-eddy turnover time $\tau = \frac{L}{u_\text{avg}}$
