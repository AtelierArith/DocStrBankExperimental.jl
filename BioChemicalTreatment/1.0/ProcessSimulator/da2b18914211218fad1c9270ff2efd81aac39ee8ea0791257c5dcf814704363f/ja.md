```
RealInputToOutflowPort(components; initial_flow=nothing, initial_concentrations=nothing, name)
```

[`OutflowPort`](@ref) に接続し、他方では [`ModelingToolkitStandardLibrary.Blocks.RealInput`s](@extref ModelingToolkitStandardLibrary.Blocks.RealInput) の一連に接続するシステムで、ModelingToolkitStandardLibrary との互換性を持ちます。このシステムは、対応するシンボル間の等価性を保証します。 [`OutflowPort`](@ref) と同じ入力を受け取ります。

!!! info
    この関数は [`ModelingToolkitStandardLibrary`](@extref ModelingToolkitStandardLibrary :doc:`index`) をロードする必要があります。このライブラリでのみ有用です。


# コネクタ

  * `outflow`: 接続する [`OutflowPort`](@ref)
  * `q`: 流量のための [`ModelingToolkitStandardLibrary.Blocks.RealInput`](@extref)
  * 流れの各成分に対して一つの [`ModelingToolkitStandardLibrary.Blocks.RealInput`](@extref)
