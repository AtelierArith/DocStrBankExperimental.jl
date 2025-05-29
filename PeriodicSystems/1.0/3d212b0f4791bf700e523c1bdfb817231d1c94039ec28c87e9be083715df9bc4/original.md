```
pcpofstab_sw(psys, ts = missing; K = 100, vinit, optimizer, maxit, vtol, Jtol, gtol, show_trace) -> (Fstab,info)
```

For a continuous-time periodic system `psys = (A(t), B(t), C(t), D(t))` of period `T` determine a periodic output feedback gain matrix  `Fstab(t)` of the same period and switching times `ts`,   such that the characteristic exponents `Λ` of the closed-loop state-matrix `A(t)+B(t)*Fstab(t)*inv(I-D(t)*Fstab(t))*C(t)` are stable.  The matrices of the system `psys` are of type `PeriodicFunctionMatrix`.  The `ns` switching times contained in the vector `ts` must satisfy `0 = ts[1] < ts[2] < ... < ts[ns] < T`.  If `ts = missing`, then `ts = [0]` is used by default (i.e., constant output feedback). 

The output feedback gain `Fstab(t)` is computed as `Fstab(t) = inv(I+F(t)D(t))*F(t)`, with `F(t)`  defined as 

```
 F(t) = F_i  for t ∈ [ts[i],ts[i+1]) and i ∈ {1, ..., ns-1} or 
 F(t) = F_ns for t ∈ [ts[ns],T)
```

where `F_i` is the `i`-th gain.   The resulting periodic matrix `Fstab(t)` is of type `PeriodicSwitchingMatrix`. The corresponding closed-loop periodic system can be obtained using the function [`psfeedback`](@ref).

For the determination of the optimal feedback gains `F_i` for `i = 1, ...., ns` an optimization-based approach is employed using  tools available in the optimization package [`Optim.jl`](https://github.com/JuliaNLSolvers/Optim.jl).  By default, the gradient-free *Nelder-Mead* local search method for unconstrained minimizations  is employed using the keyword argument setting `optimizer = Optim.NelderMead()`.    The alternative gradient-free *Simulated Annealing* global search method can be selected with `optimizer = Optim.SimulatedAnnealing()`. 

For a system with `m` inputs and `p` outputs,  an internal optimization variable `v` is used, formed as an `m×p×ns` array with `v[:,:,i] := F_i`, for `i = 1, ..., ns`.  The performance index to be minimized is `J := sdeg(v)`,  where `sdeg(v)` is the stability degree defined as the largest real part of the characteristic exponents  of `Af(t) := A(t)+B(t)*F(t)*C(t)`. The keyword argument `K` is the number of factors used to express the monodromy matrix of `Af(t)` (default: `K = 100`),  when evaluating the characteristic exponents.    By default, `v` is initialized as `v = 0` (i.e., a zero array of appropriate dimensions).  The keyword argument `vinit = v0` can be used to initialize `v` with an arbitrary `m×p×ns` array `v0`.  

The optimization process is controlled using several keyword parameters.  The keyword parameter `maxit` can be used to specify the maximum number of iterations to be performed (default: `maxit = 1000`). The keyword argument `vtol` can be used to specify the absolute tolerance in  the changes of the optimization variable `v` (default: `vtol = 0`). The keyword argument `Jtol` can be used to specify the relative tolerance in the changes of the optimization criterion `J` (default: `Jtol = 0`),  while `gtol` is the method specific main convergence tolerance (default: `gtol = 1e-3`).  With the keyword argument `show_trace = true`,  a trace of the optimization algorithm's state is shown on `stdout` (default `show_trace = false`).    (see the documentation of the [Optim.jl](https://github.com/JuliaNLSolvers/Optim.jl) package for additional information). 

The returned named tuple `info` contains `(fopt, sdeg0, sdeg, vopt, optres)`, where:

`info.fopt` is the resulting value of the optimal performance `J`;

`info.sdeg0` is the initial stability degree of the closed-loop characteristic exponents;

`info.sdeg` is the resulting stability degree of the closed-loop characteristic exponents;

`info.vopt` is the resulting value of the optimization variable `v`; 

`info.optres` is the result returned by the `Optim.optimize(...)` function of the  [`Optim.jl`](https://github.com/JuliaNLSolvers/Optim.jl) package;  several functions provided by this package can be used to inquire various information related to the optimization results (see the documention of this package). 
