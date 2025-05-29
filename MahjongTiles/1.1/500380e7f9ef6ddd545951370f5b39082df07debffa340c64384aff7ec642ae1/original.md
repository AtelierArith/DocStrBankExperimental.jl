```
wind(index)
wind(direction)
```

Creates a wind tile.  If an integer is used,  the standard Chinese ordering of the cardinal directions is used (i.e. `1` -> east, `2` -> south, `3` -> west, `4` -> north). Otherwise, symbols can also be used for the names of the directions (e.g. `:east`, `:north`).

## Example

```jldoctest
julia> wind(:north)
🀃

julia> wind(2)
🀁
```
