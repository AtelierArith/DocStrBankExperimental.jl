```
amrs = loadcurrent(outputdir::AbstractString, filesequence::AbstractVector=0:0; kwargs...)
amrs = loadcurrent(outputdir::AbstractString, fileid::Integer; kwargs...)
```

Function: load time-series of ocean current data.           The keyword arguments follow [`loadfortq`](@ref).           See also: [`loadfortt`](@ref).
