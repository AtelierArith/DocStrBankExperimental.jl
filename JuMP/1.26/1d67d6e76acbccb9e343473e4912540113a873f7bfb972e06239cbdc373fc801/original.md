```
solution_summary(model::GenericModel; result::Int = 1, verbose::Bool = false)
```

Return a struct that can be used print a summary of the solution in result `result`.

If `verbose=true`, write out the primal solution for every variable and the dual solution for every constraint, excluding those with empty names.

## Example

When called at the REPL, the summary is automatically printed:

```jldoctest
julia> model = Model();

julia> solution_summary(model)
solution_summary(; result = 1, verbose = false)
├ solver_name          : No optimizer attached.
├ Termination
│ ├ termination_status : OPTIMIZE_NOT_CALLED
│ ├ result_count       : 0
│ └ raw_status         : optimize not called
└ Solution (result = 1)
  ├ primal_status        : NO_SOLUTION
  └ dual_status          : NO_SOLUTION
```

Use `print` to force the printing of the summary from inside a function:

```jldoctest
julia> model = Model();

julia> function foo(model)
           print(solution_summary(model))
           return
       end
foo (generic function with 1 method)

julia> foo(model)
solution_summary(; result = 1, verbose = false)
├ solver_name          : No optimizer attached.
├ Termination
│ ├ termination_status : OPTIMIZE_NOT_CALLED
│ ├ result_count       : 0
│ └ raw_status         : optimize not called
└ Solution (result = 1)
  ├ primal_status        : NO_SOLUTION
  └ dual_status          : NO_SOLUTION
```
