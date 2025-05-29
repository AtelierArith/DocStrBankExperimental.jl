```
@shorthands(funcname::Symbol)
```

Defines and exports shorthand plotting method definitions (`$funcname` and `$funcname!`). Pass the series type (as a symbol) to the macro.

## Examples

```julia
# define some series type
@recipe function f(::Type{Val{:myseriestype}}, x, y)
    # some implementation here
end
# docstrings are forwarded
"""
    myseriestype(x, y)
Plot my series type!
"""
@shorthands myseriestype
```
