```
parameter_function(func::Function, 
                   pref_inputs::Union{GeneralVariableRef, AbstractArray{GeneralVariableRef}, Tuple}; 
                   [name::String = [the name of `func`]]
                   )::GeneralVariableRef
```

Make a parameter function and return a `GeneralVariableRef` that can be  embedded in InfiniteOpt expressions. This serves as a convenient wrapper for  [`build_parameter_function`](@ref) and [`add_parameter_function`](@ref). For an  even more convenient definition method see [`@parameter_function`](@ref).

Here `func` denotes the function that will take a support of infinite parameters as  input (formatted like `pref_inputs`) and will return a scalar value. Specifically,  `func` should be of the form:

```
func(paramvals...)::Float64
```

where the formatting of `paramvals` is analagous to point variables (and will be  based on the tuple of infinite parameter references given in `parameter_refs`). Moreover, `func` must be a function that returns a scalar numeric value. 

Errors if `func` will not take a support formatted like `pref_inputs` in  combination with the `fargs` and `fkwargs` specified. Also errors if `pref_inputs`  follow an invalid input format.

**Example**

```julia-repl
julia> p_func = parameter_function(sin, t)
sin(t)

julia> p_func3 = parameter_function((t_supp) -> 2 * sin(2 * t_supp), t, name = "mysin")
mysin(t)

julia> p_func4 = parameter_function(t, name = "mysin") do t_supp
                    if t_supp <= 5
                        return sin(t_supp)
                    else 
                        return 2 * sin(2 * t_supp)
                    end
                 end

mysin(t)
```
