```
struct ParameterTimeseriesIndex
function ParameterTimeseriesIndex(timeseries_idx, parameter_idx)
```

パラメータタイムシリーズオブジェクト内のタイムシリーズパラメータのタイムシリーズのインデックスを格納する構造体です。`timeseries_idx`は、パラメータが属するタイムシリーズを識別するインデックスを指します。`parameter_idx`は、そのタイムシリーズオブジェクト内のパラメータのタイムシリーズのインデックスを指します。`parameter_idx`は、特定のパラメータに対して[`parameter_index`](@ref)によって返されるオブジェクトとは異なる場合があることに注意してください。この構造体の2つのフィールドは`timeseries_idx`と`parameter_idx`です。
