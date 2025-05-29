```
@teval texpr
```

evaluates the lisp-like tuple expression `texpr`.

Example: Calculation of `sin(π/6)`

```julia
julia> @teval (:call, :sin, (:call, :/, π, 6))
0.49999999999999994
```

In some cases, you can omit `:call`.

```julia
julia> @teval (:sin, (:/, π, 6))
0.49999999999999994
```
