```
interpolate(
    x_vector::Vector{<:Union{VariableRef,AffExpr}},
    points::Vector{<:Tuple},
    sets::Vector;
    update_bounds::Bool = false,
    method::Symbol = :default,
    name::String = "",
)
```

Function that constrains the variables to lie inside the convex hull of one of the sets of points (defined by `sets`).

### Required arguments

`x_vector` vector of variables or expressions that will be used as the domain of the interpolation

`points` vector of points that define the interpolation; these points can contain real number and as well as variables and expressions.

`sets` for each point in the vector `points`, `sets` contains the name(s) of the sets that point is a member of. 

### Optional arguments

`update_bounds` is set to `true` if the upper and lower bounds of `x_vector` components should be updated based on the values in `points`.

`method` if the formulation method and can be set to `:convex`, `:SOS1`, `:binary` or `:bisection`.

`name` can be set to give the variables created meaningful names.
