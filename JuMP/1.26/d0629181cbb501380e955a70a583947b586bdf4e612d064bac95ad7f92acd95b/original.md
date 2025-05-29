```
set_value(p::NonlinearParameter, v::Number)
```

Store the value `v` in the nonlinear parameter `p`.

!!! compat
    This function is part of the legacy nonlinear interface. Consider using the new nonlinear interface documented in [Nonlinear Modeling](@ref).


## Example

```jldoctest
julia> model = Model();

julia> @NLparameter(model, p == 0)
p == 0.0

julia> set_value(p, 5)
5

julia> value(p)
5.0
```
