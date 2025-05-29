```
gpumarker(f, regiontag::AbstractString)
```

Adds a LIKWID GPU marker region around the execution of the given function `f` using [`GPUMarker.startregion`](@ref), [`GPUMarker.stopregion`](@ref) under the hood. Note that `LIKWID.GPUMarker.init()` and `LIKWID.GPUMarker.close()` must be called before and after, respectively.

# Examples

```julia
julia> using LIKWID, CUDA

julia> GPUMarker.init()

julia> gpumarker("sleeping...") do
           sleep(1)
       end
true

julia> gpumarker(()->CUDA.rand(100), "create rand vec")
true

julia> GPUMarker.close()

```
