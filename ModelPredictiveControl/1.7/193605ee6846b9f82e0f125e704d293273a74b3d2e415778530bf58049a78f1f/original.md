```
setname!(model::SimModel; u=nothing, y=nothing, d=nothing, x=nothing) -> model
```

Set the names of `model` inputs `u`, outputs `y`, disturbances `d`, and states `x`.

The keyword arguments `u`, `y`, `d`, and `x` must be vectors of strings. The strings are used in the plotting functions.

# Examples

```jldoctest
julia> model = setname!(LinModel(tf(3, [10, 1]), 2.0), u=["\$A\$ (%)"], y=["\$T\$ (∘C)"])
LinModel with a sample time Ts = 2.0 s and:
 1 manipulated inputs u
 1 states x
 1 outputs y
 0 measured disturbances d
```
