```
struct SchrodingerProblem
SchrodingerProblem(reg, tspan, hamiltonian; kw...)
```

Define a Schrodinger equation problem that uses ODE solver from `OrdinaryDiffEq` to solve the dynamics.

# Arguments

  * `register`: required, the evolution problem register, can be a [`SubspaceArrayReg`](@ref) or an `ArrayReg`   from `Yao`.
  * `tspan`: required, a `(start, stop)` tuple or a single number `t`, the single value form `t` is equivalent   to `(zero(t), t)`.
  * `hamiltonian`: required, the evolution hamiltonian, can be created via [`rydberg_h`](@ref).

# Common Keyword Arguments

  * `algo`: optional, algorithm to use, this only works for the `emulate!` interface.   for `solve` or integrator interface, one will need to specify the algorithm explicitly.
  * `progress`: print progress bar or not, this may effect the performance when problem scale is small, default is `true`.
  * `progress_steps`: steps to update the progress bar, default is `5`.
  * `reltol`: relative tolerance, default is 1e-8.
  * `abstol`: absolute tolerance, default is 1e-8.

# Further References

For more ODE options, please refer to [Common Solver Options](https://diffeq.sciml.ai/stable/basics/common_solver_opts/). The `SchrodingerProblem` type supports most of the standard DiffEq problem interface.
