```
convolved(m1::AbstractModel, m2::AbstractModel)
```

Convolve two models to create a composite [`ConvolvedModel`](@ref Comrade.ConvolvedModel).

```julia-repl
julia> m1 = Ring()
julia> m2 = Disk()
julia> convolved(m1, m2)
```
