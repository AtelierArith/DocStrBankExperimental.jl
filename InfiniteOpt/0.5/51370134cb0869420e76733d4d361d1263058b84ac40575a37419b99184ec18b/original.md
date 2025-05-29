```
fill_in_supports!(model::InfiniteModel; [num_supports::Int = DefaultNumSupports,
                  modify::Bool = true])::Nothing
```

Automatically generate support points for all infinite parameters in model. This calls `fill_in_supports!` for each parameter in the model. See [`fill_in_supports!`](@ref) for more information. Errors if one of the infinite domain types is unrecognized. Note that no supports will be added to a particular parameter if it already has some and `modify = false`.

**Example**

```julia-repl
julia> fill_in_supports!(model, num_supports = 4)

julia> supports(t)
4-element Array{Float64,1}:
 0.0
 0.333
 0.667
 1.0
```
