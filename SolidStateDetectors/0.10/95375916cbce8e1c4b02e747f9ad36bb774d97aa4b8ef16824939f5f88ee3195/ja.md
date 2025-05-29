```
ssd_read(filename::AbstractString, ::Type{Simulation})
```

指定された `filename` を使用して HDF5 ファイルから [`Simulation`](@ref) を読み込みます。これは [LegendHDF5IO.jl](https://github.com/legend-exp/LegendHDF5IO.jl) を使用しています。

## 引数

  * `filename::AbstractString`: HDF5 ファイルのファイル名。

## 例

```julia
using SolidStateDetectors
using LegendHDF5IO
sim = ssd_read("example_sim.h5", Simulation)
```

他にも [`ssd_write`](@ref) を参照してください。
