```
from_expr(::Type{T}, expr; throw_error::Bool=false, kwargs...)
```

Parses an `expr` into an object of type `T`

The provided `kwargs` are passed to the underlying parsing function. 

If `expr` cannot be parsed into an object of type `T`     - if `throw_error == true`, throws an `ArgumentError`     - otherwise, returns `nothing`  

====================

```
from_expr(::Type{Vector{T}}, expr::Expr; throw_error::Bool=false)
```

Parses a `tuple` or `vect` `expr` as a `Vector{T}`. Each argument of `expr` must be of type `T`

====================

```
from_expr(::Type{Vector{T}}, input::T; throw_error::Bool=false)
```

Returns a singleton `Vector{T}` containing `input`

====================

```
from_expr(::Type{FuncCall}, expr; normalize_kwargs::Bool=false)
```

Returns a parsed `FuncCall` from `expr`

If `normalize_kwargs = true`, trailing equality expressions (e.g., `f(a, b, c=1)` will be parsed as keyword arguments. 
