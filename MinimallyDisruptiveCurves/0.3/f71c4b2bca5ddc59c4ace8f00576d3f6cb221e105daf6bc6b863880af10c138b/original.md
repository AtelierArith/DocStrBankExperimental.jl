```
CurveDistance(timepoints::AbstractRange)
CurveDistance(timepoints::Vector{<:AbstractFloat})
```

Print @info REPL output when curve distance reaches each of the timepoints::Vector{<:AbstractFloat}

Example c = CurveDistance(0.1:0.1:2.1)

c can then be used as an argument to Verbose(), which then goes as a keyword argument into evolve.
