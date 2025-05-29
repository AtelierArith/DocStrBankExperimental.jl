```
ssd_write(filename::AbstractString, sim::Simulation)
```

[`Simulation`](@ref)を`NamedTuple`に変換し、指定された`filename`を使用してHDF5ファイルに書き込みます。[LegendHDF5IO.jl](https://github.com/legend-exp/LegendHDF5IO.jl)を使用します。

## 引数

  * `filename::AbstractString`: HDF5ファイルのファイル名。
  * `sim::Simulation`: HDF5ファイルに書き込むべき[`Simulation`](@ref)。

## 例

```julia
using SolidStateDetectors
using LegendHDF5IO
sim = Simulation(SSD_examples[:InvertedCoax])
simulate!(sim)
ssd_write("example_sim.h5", sim)
```

!!! warn
    `filename`のファイルがすでに存在する場合、このメソッドによって上書きされます。


[`ssd_read`](@ref)も参照してください。
