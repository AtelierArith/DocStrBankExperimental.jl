```
dragon(index)
dragon(name)
```

Creates a wind tile.  If an integer is used,  the standard ordering is used (i.e. `1` -> red dragon, `2` -> green dragon, `3` -> white dragon). Otherwise, symbols can also be used for their names/colors (e.g. `:red`, `:green`).

## Example

```jldoctest
julia> dragon(:red)
🀄

julia> dragon(2)
🀅
```
