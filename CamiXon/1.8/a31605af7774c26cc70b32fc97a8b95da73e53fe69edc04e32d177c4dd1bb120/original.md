```
collectSpinorbit(config::String; msg=false)
```

Collect the spinobitals specified by `config` (in standard configuration notation) into an array of spinorbitals.

#### Example:

```
julia> config = "1s²2s²2p⁶";

julia> collectSpinorbit(config; msg=true)
10-element Vector{Spinorbit}:
 Spinorbit("1s↓", 1, 0, 0, 0, -1//2)
 Spinorbit("1s↑", 1, 0, 0, 0, 1//2)
 Spinorbit("2s↓", 2, 1, 0, 0, -1//2)
 Spinorbit("2s↑", 2, 1, 0, 0, 1//2)
 Spinorbit("2p↓", 2, 0, 1, -1, -1//2)
 Spinorbit("2p↓", 2, 0, 1, 0, -1//2)
 Spinorbit("2p↓", 2, 0, 1, 1, -1//2)
 Spinorbit("2p↑", 2, 0, 1, -1, 1//2)
 Spinorbit("2p↑", 2, 0, 1, 0, 1//2)
 Spinorbit("2p↑", 2, 0, 1, 1, 1//2)
```
