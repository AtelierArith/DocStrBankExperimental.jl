```
StdDPP()
```

Standard DPP (Determinantal Point Process) sampling. The size of the returned `Z` is not fixed (but is not allowed to be empty unlike in a classical DPP). The kernel is passed as a keyword argument to [`inducingpoints`](@ref).
