```
getshiftedgenumber(shift::ShiftNet)
```

Get the edge numbers where the shifts are located, for an object [`ShiftNet`](@ref). If a shift is placed at the root node with no parent edge, the edge number of a shift is set to -1 (as if missing).
