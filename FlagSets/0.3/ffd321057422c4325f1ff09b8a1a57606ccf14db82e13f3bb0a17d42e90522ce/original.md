```
flags(x::FlagSet)
```

Return the set of flags in `x` as a `Tuple`.

# Examples

```julia
julia> @symbol_flagset FontFlags bold=1 italic=2 large=4

julia> flags(FontFlags(3))
(:bold, :italic)
```
