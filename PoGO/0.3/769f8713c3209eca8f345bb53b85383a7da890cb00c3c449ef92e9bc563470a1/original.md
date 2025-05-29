```
power(
    x::Union{VariableRef,AffExpr},
    y::Union{VariableRef,AffExpr},
    n::Int = 0;
    method::Symbol = :default,
    type::Symbol = :interior,
    name::String = "",
)
```

Function that defines a power formulation (`x^y`) for a given pair of variables or affine expressions. This function will select the best formulation, given `x` and `y`.

### Required arguments

`x` and `y` are either of type `VariableRef` or `AffExpr` and `x^y` is the power function that is being modelled.

### Optional arguments

`n` is used if the power is approximated using the difference of two squares.

`method` is used if the power is approximated using the difference of two squares. This can be set to `:binary` `:echelon` `:SOS1` or `:SOS2`.

`type` is used if the power is approximated using the difference of two squares. This can be set to `:upper` `:lower` `:interior` `cutting_planes` or `:combined`.

`name` can be set to give the variables created meaningful names.
