```
flags(T)
```

Return the set of flags of type `T` as a `Tuple`.

# Examples

```julia
julia> @flagset RoundingFlags RoundDown RoundUp RoundNearest

julia> flags(RoundingFlags)
(RoundingMode{:Down}(), RoundingMode{:Up}(), RoundingMode{:Nearest}())
```
