```
pdlqofc(psys, Q, R; S, G = I, sdeg = 1, stabilizer, optimizer, vinit, maxiter, vtol, Jtol, gtol, show_trace) -> (Fopt, info)
```

Compute for the discrete-time periodic state-space system `psys = (A(t),B(t),C(t),D(t))` of the form

```
x(t+1) = A(t)x(t) + B(t)u(t) + Bw(t)w(t) 
  y(t) = C(t)x(t) + D(t)u(t) + Dw(t)w(t) ,
```

the optimal periodic feedback gain `Fopt(t)` in the output feedback control law  

```
u(t) = Fopt(t)*y(t),
```

which minimizes the expectation of the quadratic index

```
 J = E{ Sum [x(t)'*Q(t)*x(t) + 2*x(t)'*S(t)*u(t) + u(t)'*R(t)*u(t)] },
```

where `Q(t)`, `R(t)` and `S(t)` are periodic weighting matrices.  For a system of order `n` with `m` control inputs in `u(t)` and `p` measurable outputs in `y(t)`,  `Q(t)` and `R(t)` are `n×n` and `m×m` symmetric periodic matrices, respectively, and  `S(t)` is an `n×m` periodic matrix, which can be specified via the keyword argument `S`.  By default `S = missing`, in which case, `S(t) = 0` is assumed.    The periodic matrices `Q(t)`,`R(t)` and `S(t)` have the same type as the matrices of the state-space system, i.e., either of type `PeriodicMatrix` or `PeriodicArray`.   The dimension `m` of `u(t)` is deduced from the dimension of `R(t)`.  `Q`, `R` and `S` can be alternatively provided as constant real matrices. 

The resulting `m×p` periodic output feedback gain `Fopt(t)` has the same type as the state-space system matrices and is computed as `Fopt(t) = inv(I+F(t)D(t))*F(t)`, with `F(t)`  defined as 

```
 F(t) = F_i  for i ∈ {1, ..., ns}
```

where `ns` is the number of sampling times in a period (i.e., `ns = psys.period/psys.Ts`) and `F_i` is the `i`-th gain. 

The covariance of the initial state `x(0)` can be specified via the keyword argument `G` (default: `G = I`) and a desired stability degree of the closed-loop characteristic multipliers can be specified using the keyword argument `sdeg` (default: `sdeg = 1`). 

For the determination of the optimal feedback gains `F_i` for `i = 1, ...., ns` an optimization-based approach is employed using  tools available in the optimization package [`Optim.jl`](https://github.com/JuliaNLSolvers/Optim.jl).  By default, the gradient-based limited-memory quasi-Newton method (also known as `L-BFGS`) for unconstrained minimizations  is employed using the keyword argument setting `optimizer = LBFGS(;alphaguess = LineSearches.InitialStatic(;scaled=true))`, where  an initial step length for the line search algorithm is chosen using the keyword argument `alphaguess`  (see the [`LineSearches.jl`](https://github.com/JuliaNLSolvers/LineSearches.jl) package for alternative options).  The employed default line search algorithm is `HagerZhang()` and an alternative method can be specified using the keyword argument `linesearch`  (e.g., `linesearch = LineSearches.MoreThuente()`).   Alternative gradient-based methods can be also selected, such as, for example,  the quasi-Newton method `BFGS` with `optimizer = Optim.BFGS()`, or  for small size optimization problems, the Nelder-Mead gradient-free method with `optimizer = Optim.NelderMead()`.  For the computation of the function `J` and its gradient  `∇J`, the formulas developed in [1] for stable systems are used. Each evaluation involves the solution of  of a pair of periodic Lyapunov difference equations using the method proposed in [2].   If the original system `psys` is unstable, the computation of a stabilizing feedback is performed using the same optimization techniques applied iteratively to systems  with modified state matrices of the form  `A(t)/α` and control matrices `B(t)/α`, where `α ≥ 1` is chosen such that `A(t)/α` is stable, and the values of `α` are successively decreased until the stabilization is achieved with `α = 1`. The optimization method for stabilization can be independently selected using the keyword argument `stabilizer`, with the default setting   `stabilizer = LBFGS(;alphaguess = LineSearches.InitialStatic(;scaled=true))`. If only stabilization is desired, then use  `optimizer = nothing`. 

An internal optimization variable `v` is used, formed as an `m×p×ns` array with `v[:,:,i] := F_i`, for `i = 1, ..., ns`.  By default, `v` is initialized as `v = 0` (i.e., a zero array of appropriate dimensions).  The keyword argument `vinit = v0` can be used to initialize `v` with an arbitrary `m×p×ns` real array `v0`.   

The optimization process is controlled using several keyword parameters.  The keyword parameter `maxiter = maxit` can be used to specify the maximum number of iterations to be performed (default: `maxit = 1000`). The keyword argument `vtol` can be used to specify the absolute tolerance in  the changes of the optimization variable `v` (default: `vtol = 0`). The keyword argument `Jtol` can be used to specify the relative tolerance in the changes of the optimization criterion `J` (default: `Jtol = 0`),  while `gtol` can be used to specify the absolute tolerance in the gradient `∇J`, in infinity norm (default: `gtol = 1e-5`).  With the keyword argument `show_trace = true`,  a trace of the optimization algorithm's state is shown on `stdout` (default `show_trace = false`).    For stabilization purposes, the values `Jtol = 1.e-3`, `gtol = 1.e-2`, `maxit = 20` are used to favor faster convergence. 

The returned named tuple `info` contains `(fopt, sdeg0, sdeg, vopt, optres)`, where:

`info.fopt` is the resulting value of the optimal performance `J`;

`info.sdeg0` is the initial stability degree of the closed-loop characteristic multipliers;

`info.sdeg` is the resulting stability degree of the closed-loop characteristic multipliers;

`info.vopt` is the resulting value of the optimization variable `v`; 

`info.optres` is the result returned by the `Optim.optimize(...)` function of the  [`Optim.jl`](https://github.com/JuliaNLSolvers/Optim.jl) package;  several functions provided by this package can be used to inquire various information related to the optimization results (see the documention of this package). 

A bound-constrained optimization can be performed using the keyword argument `lub = (lb, ub)`, where `lb` is the lower bound and `ub` is the upper bound on the feedback gains.  By default,  `lub = missing` in which case the bounds `lb = -Inf` and `ub = Inf` are assumed. 

*References*     

[1] A. Varga and S. Pieters. Gradient-based approach to solve optimal periodic output feedback problems.      Automatica, vol.34, pp. 477-481, 1998.

[2] A. Varga. Periodic Lyapunov equations: some applications and new algorithms.                Int. J. Control, vol, 67, pp, 69-87, 1997.
