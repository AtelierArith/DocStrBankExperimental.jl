```julia
FunctionCallingCallback(func;
    funcat = Vector{Float64}(),
    func_everystep = isempty(funcat),
    func_start = true,
    tdir = 1)
```

The function calling callback lets you define a function `func(u,t,integrator)` which gets called at the time points of interest. The constructor is:

  * `func(u, t, integrator)` is the function to be called.
  * `funcat` values or interval that the function is sure to be evaluated at.
  * `func_everystep` whether to call the function after each integrator step.
  * `func_start` whether the function is called at the initial condition.
  * `tdir` should be `sign(tspan[end]-tspan[1])`. It defaults to `1` and should be adapted if `tspan[1] > tspan[end]`.
