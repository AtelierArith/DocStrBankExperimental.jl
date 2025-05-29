```
lb, ub = getbounds(p::AbstractVector)
```

Return vectors of lower and upper bounds of parameter vector `p`. Create parameters with bounds like this

```
@parameters p [bounds=(-1, 1)]
```

See also [`tunable_parameters`](@ref), [`hasbounds`](@ref)
