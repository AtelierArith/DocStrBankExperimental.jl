```
struct PyHFModel{E, O, P} <: AbstractModel
    expected::E
    observed::O
    priors::P
    prior_names
    inits::Vector{Float64}
end
```

Struct for holding result from [build_pyhf](@ref). List of accessor functions is 

  * expected(p::PyHFModel)
  * observed(p::PyHFModel)
  * priors(p::PyHFModel)
  * prior_names(p::PyHFModel)
  * inits(p::PyHFModel)
