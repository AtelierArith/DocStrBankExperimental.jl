```
newton_raphson(func::Function, 
    u0::Union{Array,PyObject}, 
    θ::Union{Missing,PyObject, Array{<:Real}}=missing,
    args::PyObject...) where T<:Real
```

Newton Raphson solver for solving a nonlinear equation.  ∘ `func` has the signature 

  * `func(θ::Union{Missing,PyObject}, u::PyObject)->(r::PyObject, A::Union{PyObject,SparseTensor})` (if `linesearch` is off)
  * `func(θ::Union{Missing,PyObject}, u::PyObject)->(fval::PyObject, r::PyObject, A::Union{PyObject,SparseTensor})` (if `linesearch` is on)

where `r` is the residual and `A` is the Jacobian matrix; in the case where `linesearch` is on, the function value `fval` must also be supplied. ∘ `θ` are external parameters. ∘ `u0` is the initial guess for `u` ∘ `args`: additional inputs to the func function  ∘ `kwargs`: keyword arguments to `func`

The solution can be configured via `ADCME.options.newton_raphson`

  * `max_iter`: maximum number of iterations (default=100)
  * `rtol`: relative tolerance for termination (default=1e-12)
  * `tol`: absolute tolerance for termination (default=1e-12)
  * `LM`: a float number, Levenberg-Marquardt modification $x^{k+1} = x^k - (J^k + \mu^k)^{-1}g^k$ (default=0.0)
  * `linesearch`: whether linesearch is used (default=false)

Currently, the backtracing algorithm is implemented. The parameters for `linesearch` are supplied via `options.newton_raphson.linesearch_options`

  * `c1`: stop criterion, $f(x^k) < f(0) + \alpha c_1  f'(0)$
  * `ρ_hi`: the new step size $\alpha_1\leq \rho_{hi}\alpha_0$
  * `ρ_lo`: the new step size $\alpha_1\geq \rho_{lo}\alpha_0$
  * `iterations`: maximum number of iterations for linesearch
  * `maxstep`: maximum allowable steps
  * `αinitial`: initial guess for the step size $\alpha$
