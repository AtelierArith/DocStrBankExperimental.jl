```
LinFitness(coefs::AbstractVector{<:Real})
```

Used to define a linear fitness function  measuring the quality of an output `y` of the objective function.

May provide better performance than the more general `NonlinFitness` as some acquisition functions can be calculated analytically with linear fitness functions whereas this may not be possible with a nonlinear fitness function.

See also: [`NonlinFitness`](@ref)

# Example

A fitness function `f(y) = y[1] + a * y[2] + b * y[3]` can be defined as:

```julia-repl
julia> LinFitness([1., a, b])
```
