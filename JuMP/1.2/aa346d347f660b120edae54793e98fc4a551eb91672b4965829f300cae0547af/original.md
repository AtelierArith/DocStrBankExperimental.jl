```
solution_summary(model::Model; verbose::Bool = false)
```

Return a struct that can be used print a summary of the solution.

If `verbose=true`, write out the primal solution for every variable and the dual solution for every constraint, excluding those with empty names.

## Examples

When called at the REPL, the summary is automatically printed:

```julia
julia> solution_summary(model)
[...]
```

Use `print` to force the printing of the summary from inside a function:

```julia
function foo(model)
    print(solution_summary(model))
    return
end
```
