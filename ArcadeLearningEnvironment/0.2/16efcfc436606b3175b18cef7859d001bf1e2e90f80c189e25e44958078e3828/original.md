```
getROMList()
```

Returns an array of names of ROMs available. These ROMS can be loaded by simply passing their name to the [`loadROM`](@ref) function, as opposed to passing their full path.

# Example

```julia-repl
julia> getROMList()
74-element Array{String,1}:
 "adventure"
 "air_raid"
 "alien"
 "amidar"
 "assault"
 "asterix"
 ⋮
 "venture"
 "video_pinball"
 "wizard_of_wor"
 "yars_revenge"
 "zaxxon"
```
