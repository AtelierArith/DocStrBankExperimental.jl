```
add_parameter_function(model::InfiniteModel, pfunc::ParameterFunction, 
                       [name::String])::GeneralVariableRef
```

Add an [`ParameterFunction`](@ref) `pfunc` to the `model` using `name` for  printing and return a `GeneralVariableRef` such that it can be embedded in  expressions. Errors if the parameter function `pfunc` points to do not belong to  `model`. Note that `pfunc` should be created using [`build_parameter_function`](@ref).

**Example**

```julia-repl
julia> f = build_parameter_function(error, sin, t);

julia> fref = add_parameter_function(model, f)
sin(t)
```
