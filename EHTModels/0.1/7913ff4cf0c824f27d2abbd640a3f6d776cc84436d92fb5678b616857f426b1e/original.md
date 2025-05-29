```
components(m::AbstractModel)
```

Returns the model components for a composite model. This will return a Tuple with all the models you have constructed.

# Example

```julia-repl
julia> m = Gaussian() + Disk()
julia> components(m)
(Gaussian{Float64}(), Disk{Float64}())
```
