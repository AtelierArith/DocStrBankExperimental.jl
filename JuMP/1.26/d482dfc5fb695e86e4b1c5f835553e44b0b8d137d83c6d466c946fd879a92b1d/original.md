```
assert_is_solved_and_feasible(model::GenericModel; kwargs...)
```

A function calls [`is_solved_and_feasible`](@ref) and, if the return is `false`, errors with an informative error message describing the state of the solver.

## Keyword arguments

See [`is_solved_and_feasible`](@ref) for a description of all keyword arguments.

## Example

```jldoctest
julia> import Ipopt

julia> model = Model(Ipopt.Optimizer);

julia> is_solved_and_feasible(model)
false

julia> assert_is_solved_and_feasible(model)
ERROR: The model was not solved correctly. Here is the output of `solution_summary` to help debug why this happened:

solution_summary(; result = 1, verbose = false)
├ solver_name          : Ipopt
├ Termination
│ ├ termination_status : OPTIMIZE_NOT_CALLED
│ ├ result_count       : 0
│ └ raw_status         : optimize not called
└ Solution (result = 1)
  ├ primal_status        : NO_SOLUTION
  └ dual_status          : NO_SOLUTION

Stacktrace:
[...]
```
