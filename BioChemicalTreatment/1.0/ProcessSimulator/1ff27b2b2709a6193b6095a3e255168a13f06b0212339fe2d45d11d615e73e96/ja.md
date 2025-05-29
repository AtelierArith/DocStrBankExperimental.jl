```
RealInputToStateOutput(components; initial_state=nothing, name)
```

[`StateOutputPort`](@ref) に接続し、他方では ModelingToolkitStandardLibrary との互換性のために一連の [`ModelingToolkitStandardLibrary.Blocks.RealInput`s](@extref ModelingToolkitStandardLibrary.Blocks.RealInput) に接続するシステムです。このシステムは、対応するシンボル間の等価性を保証します。 [`StateOutputPort`](@ref) と同じ入力を受け取ります。

!!! info
    この関数は、[`ModelingToolkitStandardLibrary`](@extref ModelingToolkitStandardLibrary :doc:`index`) がロードされている必要があります。このライブラリでのみ有用です。


# コネクタ

  * `stateoutput`: 接続する [`StateOutputPort`](@ref)
  * 各状態に対して1つの [`ModelingToolkitStandardLibrary.Blocks.RealInput`](@extref)
