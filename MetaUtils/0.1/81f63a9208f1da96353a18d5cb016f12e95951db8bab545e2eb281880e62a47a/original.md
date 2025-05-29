```
teval(texpr, m::Module=Main)
```

evaluates the lisp-like tuple expression `texpr`.

Example: Calculation of `sin(π/6)`

```julia
julia> (:call, :sin, (:call, :/, π, 6)) |> teval
0.49999999999999994
```

In some cases, you can omit `:call`.

```julia
julia> (:sin, (:/, π, 6)) |> teval
0.49999999999999994
```
