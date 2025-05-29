```
gpumarker(f, regiontag::AbstractString)
```

指定された関数 `f` の実行の周りに LIKWID GPU マーカー領域を追加します。内部では [`GPUMarker.startregion`](@ref) と [`GPUMarker.stopregion`](@ref) を使用します。`LIKWID.GPUMarker.init()` と `LIKWID.GPUMarker.close()` は、それぞれ前後に呼び出す必要があります。

# 例

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
