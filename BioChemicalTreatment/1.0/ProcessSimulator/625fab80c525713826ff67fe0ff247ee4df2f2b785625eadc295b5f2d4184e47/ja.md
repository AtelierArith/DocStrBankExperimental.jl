```
StateInputToRealOutput(components; initial_rates=nothing, name)
```

[`StateInputPort`](@ref)に接続し、他方では[`ModelingToolkitStandardLibrary.Blocks.RealOutput`s](@extref ModelingToolkitStandardLibrary.Blocks.RealOutput)の一連に接続するシステムで、ModelingToolkitStandardLibraryとの互換性を持ちます。このシステムは、対応するシンボル間の等価性を保証します。[`StateInputPort`](@ref)と同じ入力を受け取ります。

!!! info
    この関数は[`ModelingToolkitStandardLibrary`](@extref ModelingToolkitStandardLibrary :doc:`index`)をロードする必要があります。このライブラリでのみ有用です。


# コネクタ

  * `stateinput`: 接続する[`StateInputPort`](@ref)
  * 各コンポーネントに対して1つの[`ModelingToolkitStandardLibrary.Blocks.RealOutput`](@extref)
