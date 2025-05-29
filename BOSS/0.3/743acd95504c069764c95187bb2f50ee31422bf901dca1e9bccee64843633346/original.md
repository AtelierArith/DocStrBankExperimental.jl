```
NonlinFitness(fitness::Function)
```

Used to define a general nonlinear fitness function measuring the quality of an output `y` of the objective function.

If your fitness function is linear, use `LinFitness` which may provide better performance.

See also: [`LinFitness`](@ref)

# Example

```julia-repl
julia> NonlinFitness(y -> cos(y[1]) + sin(y[2]))
```
