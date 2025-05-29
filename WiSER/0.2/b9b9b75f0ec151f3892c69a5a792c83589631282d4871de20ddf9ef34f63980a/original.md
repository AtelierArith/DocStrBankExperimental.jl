```
fit!(m::WSVarLmmModel, 
solver=IpoptSolver(print_level=0, mehrotra_algorithm="yes", max_iter=100);
init=init_ls!(m), runs = 2)
```

Fit a `WSVarLmmModel` object using a weighted NLS method.

# Positional arguments

  * `m::WSVarLmmModel`: Model to fit.
  * `solver`: Nonlinear programming solver to use. Common choices include:  

      * `Ipopt.IpoptSolver(print_level=0, mehrotra_algorithm="yes", warm_start_init_point="yes", max_iter=100)`.
      * `Ipopt.IpoptSolver(print_level=0, watchdog_shortened_iter_trigger=3, max_iter=100)`.
      * `Ipopt.IpoptSolver(print_level=0, max_iter=100)`.
      * `KNITRO.KnitroSolver(outlev=3)`. (Knitro is commercial software)
      * `NLopt.NLoptSolver(algorithm=:LD_MMA, maxeval=4000)`.
      * `NLopt.NLoptSolver(algorithm=:LD_LBFGS, maxeval=4000)`.

# Keyword arguments

  * `init`: Initialization strategy. `fit!` will use `m.τ` and `m.Lγ` to set the    weight matrices `Vi` and solve the weighted NLS to obtain an   estimate for `m.β`, `m.τ`, and `m.Lγ`.  Choices for `init` include  

      * `init_ls!(m)` (default): initialize by the least squares analytical solution.
      * `init_mom!(m)`: initialize by the unweighted NLS (MoM).
      * `m`: initilize from user supplied values in `m.τ` and `m.Lγ`.
  * `runs::Integer`: Number of weighted NLS runs; default is 2. Each run will use the    newest `m.τ` and `m.Lγ` to update the weight matrices `Vi` and solve the    new weighted NLS.
  * `parallel::Bool`: Multi-threading or not. Default is `false`.
  * `verbose::Bool`: Verbose display or not, Default is `true`.
