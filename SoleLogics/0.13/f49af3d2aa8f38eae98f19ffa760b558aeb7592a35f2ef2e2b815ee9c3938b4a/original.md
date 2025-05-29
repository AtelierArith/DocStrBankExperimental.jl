```
istop(::Truth)::Bool
```

Return true if the `Truth` value is the top of its algebra. For example, in the crisp case, with `Bool` truth values, it is:

```
istop(t::Bool)::Bool = (t == true)
```

See also [`isbot`](@ref), [`Truth`](@ref).
