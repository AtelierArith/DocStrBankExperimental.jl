```
add_parameter(model::InfiniteModel, p::FiniteParameter,
              [name::String = ""])::GeneralVariableRef
```

Returns a [`GeneralVariableRef`](@ref) associated with the parameter `p` that is  added to `model`. This adds a parameter to the model in a manner similar to `JuMP.add_variable`. This is to add parameters with the use of  [`@finite_parameter`](@ref).  [`build_parameter`](@ref build_parameter(::Function, ::Real)) should be used to construct `p`.

**Example**

```julia-repl
julia> p = build_parameter(error, 42);

julia> param_ref = add_parameter(model, p, "name")
name
```
