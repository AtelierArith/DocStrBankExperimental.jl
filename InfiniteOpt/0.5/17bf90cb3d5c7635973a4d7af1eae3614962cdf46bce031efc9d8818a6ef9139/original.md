```
add_parameter(model::InfiniteModel, p::IndependentParameter,
              [name::String = ""])::GeneralVariableRef
```

Returns a [`GeneralVariableRef`](@ref) associated with the parameter `p` that is added  to `model`. This adds a parameter to the model in a manner similar to  `JuMP.add_variable`. This is used to add parameters with the use of  [`@infinite_parameter`](@ref).  [`build_parameter`](@ref build_parameter(::Function, ::InfiniteScalarDomain))  should be used to construct `p`.

**Example**

```julia-repl
julia> p = build_parameter(error, IntervalDomain(0, 3), supports = Vector(0:3));

julia> param_ref = add_parameter(model, p, "name")
name
```
