```
isbot(::Truth)::Bool
```

Return true if the `Truth` value is the bottom of its algebra. For example, in the crisp case, with `Bool` truth values, it is:

```
isbot(t::Bool)::Bool = (t == false)
```

See also [`istop`](@ref), [`Truth`](@ref).
