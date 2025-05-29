コードを[`GPUMarker.startregion`](@ref)と[`GPUMarker.stopregion`](@ref)で囲むための便利なマクロです。

# 例

```julia
julia> using LIKWID, CUDA

julia> GPUMarker.init()

julia> @gpumarker "sleeping..." sleep(1)
true

julia> @gpumarker "create rand vec" CUDA.rand(100)
true

julia> GPUMarker.close()

```
