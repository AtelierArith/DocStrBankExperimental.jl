```
builtin_nothrow(𝕃::AbstractLattice, f::Builtin, argtypes::Vector{Any}, rt) -> Bool
```

Compute throw-ness of a builtin function call. `argtypes` should not include `f` itself.
