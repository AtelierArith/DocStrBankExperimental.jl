```
pdlqofc_sw(psys, Q, R, ns; S, vinit, kwargs...) -> (Fopt, info)
```

Compute for the discrete-time periodic state-space system `psys = (A(t),B(t),C(t),D(t))` of the form

x(t+1) = A(t)x(t) + B(t)u(t) + Bw(t)w(t)       y(t) = C(t)x(t) + D(t)u(t) + Dw(t)w(t) ,

the optimal switching periodic feedback gain `Fopt(t)` in the output feedback control law  

```
u(t) = Fopt(t)*y(t),
```

which minimizes the expectation of the quadratic index 

```
 J = E{ Sum [x(t)'*Q(t)*x(t) + 2*x(t)'*S(t)*u(t) + u(t)'*R(t)*u(t)] },
```

where `Q(t)`, `R(t)` and `S(t)` are periodic weighting matrices.  For a system of order `n` with `m` control inputs in `u(t)` and `p` measurable outputs in `y(t)`,  `Q(t)` and `R(t)` are `n×n` and `m×m` symmetric periodic matrices, respectively, and  `S(t)` is an `n×m` periodic matrix, which can be specified via the keyword argument `S`.  By default `S = missing`, in which case, `S(t) = 0` is assumed.    The periodic matrices `Q(t)`,`R(t)` and `S(t)` have the same type as the matrices of the state-space system, i.e., either of type `PeriodicMatrix` or `PeriodicArray`.   The dimension `m` of `u(t)` is deduced from the dimension of `R(t)`.  `Q`, `R` and `S` can be alternatively provided as constant real matrices. 

The switching times for the resulting switching periodic gain `Fopt(t)` are specified by the  `N`-dimensional integer vector `ns`.  By default, `ns = 1:N`, where `N` is the maximal number of samples (i.e., `N = psys.period/psys.Ts`). 

The resulting `m×p` periodic output feedback gain `Fopt(t)` has the type `SwitchingPeriodicArray` and is computed as `Fopt(t) = inv(I+F(t)D(t))*F(t)`, with `F(t)`  defined as 

```
 F(t) = F_i for t ∈ [ns[i]Δ,ns[i+1]Δ) and i ∈ {1, ..., N-1}, or
 F(t) = F_N for t ∈ [ns[N]Δ,T),
```

where `T` is the system period (i.e., `T = psys.period`), `Δ` is the system sampling time (i.e., `Δ = psys.Ts`)  and `F_i` is the `i`-th gain. 

If an initial value for the optimization variable `v` is provided using the keyword argument `vinit = gains`, then `gains` must be an `m×p×N` array, where `m` and `p` are the numbers of system control inputs and outputs. By default, `vinit = missing`, in which case a zero matrix `gains = 0` is assumed.  

The rest of keyword arguments contained in `kwargs` are the same as those used for the function [`pdlqofc`](@ref).  See its documentation for the description of all keyword arguments. 

The computation of gradient fully exploits the switching structure of the feedback gain, using formulas which generalize the case of constant feedback considered in [1].     

*References*     

[1] A. Varga and S. Pieters. Gradient-based approach to solve optimal periodic output feedback problems.      Automatica, vol.34, pp. 477-481, 1998.
