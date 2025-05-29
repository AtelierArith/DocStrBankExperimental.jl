Convenience macro for flanking code with [`GPUMarker.startregion`](@ref) and [`GPUMarker.stopregion`](@ref).

# Examples

```julia
julia> using LIKWID, CUDA

julia> GPUMarker.init()

julia> @gpumarker "sleeping..." sleep(1)
true

julia> @gpumarker "create rand vec" CUDA.rand(100)
true

julia> GPUMarker.close()

```
