```
struct ETDRK4TimeStepper{T,TL} <: AbstractTimeStepper{T}
```

A 4th-order exponential-time-differencing Runge-Kutta timestepper for time-stepping `∂u/∂t = L * u + N(u)`. The scheme treats the linear term `L` exactly while for the nonlinear terms `N(u)` it uses a 4th-order Runge-Kutta scheme ([`RK4TimeStepper`](@ref)). That is,

```julia
uⁿ⁺¹ = exp(L * dt) * uⁿ + RK4(N(uⁿ))
```

For more info refer to [Kassam-Trefethen-2005](@citet).
