```julia
processor(
    initialize
) -> NamedTuple{(:initialize, :finalize), <:Tuple{Any, IncompressibleNavierStokes.var"#283#284"}}
processor(
    initialize,
    finalize
) -> NamedTuple{(:initialize, :finalize), <:Tuple{Any, Any}}

```

Process results from time stepping. Before time stepping, the `initialize` function is called on an observable of the time stepper `state`, returning `initialized`. The observable is updated every time step.

After timestepping, the `finalize` function is called on `initialized` and the final `state`.

See the following example:

```julia
function initialize(state)
    s = 0
    println("Let's sum up the time steps")
    on(state) do (; n, t)
        println("The summand is $n, the time is $t")
        s = s + n
    end
    s
end

finalize(i, state) = println("The final sum (at time t=$(state.t)) is $s")
p = processor(initialize, finalize)
```

When solved for 6 time steps from t=0 to t=2 the displayed output is

```
Let's sum up the time steps
The summand is 0, the time is 0.0
The summand is 1, the time is 0.4
The summand is 2, the time is 0.8
The summand is 3, the time is 1.2
The summand is 4, the time is 1.6
The summand is 5, the time is 2.0
The final sum (at time t=2.0) is 15
```
