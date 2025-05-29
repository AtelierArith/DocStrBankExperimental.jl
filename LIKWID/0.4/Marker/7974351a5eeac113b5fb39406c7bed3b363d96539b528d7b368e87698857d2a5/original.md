```
marker(f, regiontag::AbstractString)
```

Adds a LIKWID marker region around the execution of the given function `f` using [`Marker.startregion`](@ref), [`Marker.stopregion`](@ref) under the hood. Note that `LIKWID.Marker.init()` and `LIKWID.Marker.close()` must be called before and after, respectively.

# Examples

```julia
julia> using LIKWID

julia> Marker.init()

julia> marker("sleeping...") do
           sleep(1)
       end
true

julia> marker(()->rand(100), "create rand vec")
true

julia> Marker.close()

```
