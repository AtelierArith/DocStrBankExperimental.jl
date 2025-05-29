```
offsets(x)
```

Return an `SVector` of `NTuple{N,Int}`, containing all positions in the stencil as offsets from the central cell.

Custom `Stencil`s must define this method.
