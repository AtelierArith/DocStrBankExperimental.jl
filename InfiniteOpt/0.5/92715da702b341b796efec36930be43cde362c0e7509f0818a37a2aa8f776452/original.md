```
add_derivative(model::InfiniteModel, d::Derivative, 
               [name::String = ""])::GeneralVariableRef
```

Adds a derivative `d` to `model` and returns a `GeneralVariableRef` that points  to it. Errors if the derivative dependencies do not belong to `model`. Note that  `d` should be built using [`build_derivative`](@ref) to avoid nuance internal  errors.

**Example**

```julia-repl
julia> @infinite_parameter(m, t in [0, 1]); @variable(m, x, Infinite(t));

julia> info = VariableInfo(false, 0, false, 0, false, 0, false, 0, false, false);

julia> d = build_derivative(error, info, x, t);

julia> dref = add_derivative(m, d)
∂/∂t[x(t)]
```
