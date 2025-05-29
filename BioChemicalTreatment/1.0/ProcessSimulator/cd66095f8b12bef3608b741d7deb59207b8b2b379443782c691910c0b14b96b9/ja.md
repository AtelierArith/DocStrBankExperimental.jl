```
ReactionInputToRealOutput(components; initial_rates=nothing, name)
```

[`ReactionInputPort`](@ref) に接続し、他方では [`ModelingToolkitStandardLibrary.Blocks.RealOutput`s](@extref ModelingToolkitStandardLibrary.Blocks.RealOutput) の一連に接続するシステムで、ModelingToolkitStandardLibrary との互換性を持ちます。このシステムは、対応するシンボル間の等価性を保証します。 [`ReactionInputPort`](@ref) と同じ入力を受け取ります。

!!! info
    この関数は、[`ModelingToolkitStandardLibrary`](@extref ModelingToolkitStandardLibrary :doc:`index`) がロードされている必要があります。このライブラリと一緒でのみ有用です。


# コネクタ

  * `reactioninput`: 接続する [`ReactionInputPort`](@ref)
  * 各コンポーネントに対して一つの [`ModelingToolkitStandardLibrary.Blocks.RealOutput`](@extref)
