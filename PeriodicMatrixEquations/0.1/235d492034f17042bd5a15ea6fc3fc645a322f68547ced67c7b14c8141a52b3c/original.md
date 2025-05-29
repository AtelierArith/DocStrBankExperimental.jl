```
tvcric_eval(t, W, A, R, Q; adj, solver, reltol, abstol, dt) -> Xval
```

Compute the time value `Xval := X(t)` of the solution of the periodic Riccati differential equation

```
  .                                                
  X(t) = A(t)X(t) + X(t)A(t)' + Q(t) - X(t)R(t)X(t) ,  X(t0) = W(t0), t0 < t, if adj = false (default),
```

or 

```
  .                                                
 -X(t) = A(t)'X(t) + X(t)A(t) + Q(t) - X(t)R(t)X(t) ,  X(t0) = W(t0), t0 > t, if adj = true,
```

using the periodic generator `W` determined with the function [`pgcric`](@ref) for the same periodic matrices `A`, `R` and `Q` and the same value of the keyword argument `adj`.  The initial time `t0` is the nearest time grid value to `t`, from below, if `adj = false`, or from above, if `adj = true`.  The resulting `Xval` is a symmetric matrix. 

The ODE solver to be employed can be specified using the keyword argument `solver`,  (default: `solver = "non-stiff"`) together with the required relative accuracy `reltol` (default: `reltol = 1.e-4`) and absolute accuracy `abstol` (default: `abstol = 1.e-7`).  Depending on the desired relative accuracy `reltol`, lower order solvers are employed for `reltol >= 1.e-4`,  which are generally very efficient, but less accurate. If `reltol < 1.e-4`, higher order solvers are employed able to cope with high accuracy demands. 

The following solvers from the [OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl) package can be selected:

`solver = "non-stiff"` - use a solver for non-stiff problems (`Tsit5()` or `Vern9()`);

`solver = "stiff"` - use a solver for stiff problems (`Rodas4()` or `KenCarp58()`);

`solver = "auto"` - use the default solver, which automatically detects stiff problems (`AutoTsit5(Rosenbrock23())` or `AutoVern9(Rodas5())`). 
