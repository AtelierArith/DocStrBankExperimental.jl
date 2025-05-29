```
InflowPortToRealOutput(components; initial_flow=nothing, initial_concentrations=nothing, name)
```

[`InflowPort`](@ref) に接続し、他方では ModelingToolkitStandardLibrary との互換性のために一連の [`ModelingToolkitStandardLibrary.Blocks.RealOutput`s](@extref ModelingToolkitStandardLibrary.Blocks.RealOutput) に接続するシステムです。内部的に方程式は対応するシンボル間の等式を保証します。入力は [`InflowPort`](@ref) と同じです。

!!! info
    この関数は [`ModelingToolkitStandardLibrary`](@extref ModelingToolkitStandardLibrary :doc:`index`) をロードする必要があります。このライブラリと一緒でのみ有用です。


# コネクタ

  * `inflow`: 接続する [`InflowPort`](@ref)
  * `q`: 流量のための [`ModelingToolkitStandardLibrary.Blocks.RealOutput`](@extref)
  * 流れの各成分に対して一つの [`ModelingToolkitStandardLibrary.Blocks.RealOutput`](@extref)
