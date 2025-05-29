```
Restart(optimizer, every=100)
```

Resets the `optimizer` every specified number of iterations (100 by default).

### Example

```julia-repl
julia> f, bounds, _ = Metaheuristics.TestProblems.rastrigin();

julia> optimize(f, bounds, Restart(ECA(), every=200))
```

### Customization

The restart condition can be updated by overloading the `restart_condition` method:

```julia
function Metaheuristics.restart_condition(status, restart::Restart, information, options)
    st.iteration % params.every == 0
end
```
