```
ODEIntegrator
```

Fundamental `struct` allowing interactively stepping through the numerical solving of a differential equation. The full documentation is hosted here: [https://diffeq.sciml.ai/latest/basics/integrator/](https://diffeq.sciml.ai/latest/basics/integrator/). This docstring describes basic functionality only!

Initialize using `integrator = init(prob::ODEProblem, alg; kwargs...)`. The keyword args which are accepted are the same [common solver options](https://diffeq.sciml.ai/latest/basics/common_solver_opts/) used by `solve`.

For reference, relevant fields of the `ODEIntegrator` are:

  * `t` - time of the proposed step
  * `u` - value at the proposed step
  * `opts` - common solver options
  * `alg` - the algorithm associated with the solution
  * `f` - the function being solved
  * `sol` - the current state of the solution
  * `tprev` - the last timepoint
  * `uprev` - the value at the last timepoint

`opts` holds all of the common solver options, and can be mutated to change the solver characteristics. For example, to modify the absolute tolerance for the future timesteps, one can do:

```julia
integrator.opts.abstol = 1e-9
```

For more info see the linked documentation page.
