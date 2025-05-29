Abstract supertype of [`LinModel`](@ref) and [`NonLinModel`](@ref) types.

---

```
(model::SimModel)(d=[]) -> y
```

Functor allowing callable `SimModel` object as an alias for [`evaloutput`](@ref).

# Examples

```jldoctest
julia> model = NonLinModel((x,u,_,_)->-x + u, (x,_,_)->x .+ 20, 4, 1, 1, 1, solver=nothing);

julia> y = model()
1-element Vector{Float64}:
 20.0
```
