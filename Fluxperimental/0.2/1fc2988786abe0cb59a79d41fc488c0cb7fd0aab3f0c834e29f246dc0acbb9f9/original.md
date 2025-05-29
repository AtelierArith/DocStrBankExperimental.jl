```
NoShow(layer)
NoShow(string, layer)
```

This alters printing (for instance at the REPL prompt) to let you hide the complexity of some part of a Flux model. It has no effect on the actual running of the model.

By default it prints `NoShow(...)` instead of the given layer. If you provide a string, it prints that instead – it can be anything, but it may make sense to print the name of a function which will re-create the same structure.

# Examples

```jldoctest
julia> Chain(Dense(2 => 3), NoShow(Parallel(vcat, Dense(3 => 4), Dense(3 => 5))), Dense(9 => 10))
Chain(
  Dense(2 => 3),                        # 9 parameters
  NoShow(...),                          # 36 parameters
  Dense(9 => 10),                       # 100 parameters
)                   # Total: 8 arrays, 145 parameters, 1.191 KiB.

julia> pseudolayer((i,o)::Pair) = NoShow(
                                    "pseudolayer($i => $o)",
                                    Parallel(+, Dense(i => o, relu), Dense(i => o, tanh)),
                                  )
pseudolayer (generic function with 1 method)

julia> Chain(Dense(2 => 3), pseudolayer(3 => 10), Dense(9 => 10))
Chain(
  Dense(2 => 3),                        # 9 parameters
  pseudolayer(3 => 10),                 # 80 parameters
  Dense(9 => 10),                       # 100 parameters
)                   # Total: 8 arrays, 189 parameters, 1.379 KiB.
```
