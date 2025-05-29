```
@timescale scale [parent[, oneway]]
```

Define a new time scale and the corresponding `Epoch` type alias.

### Arguments

  * `scale`: The name of the time scale
  * `parent`: The "parent" time scale to which it should be linked (optional)
  * `oneway`: If `true`, only the transformation from `parent` to `scale` is   registered (optional, default: `false`)

# Example

```jldoctest; setup = :(using AstroTime)
julia> @timescale GMT TAI

julia> GMT isa TimeScale
true

julia> GMTEpoch
Epoch{GMTScale}

julia> find_path(TT, GMT)
3-element Vector{TimeScale}:
 TT
 TAI
 GMT
```
