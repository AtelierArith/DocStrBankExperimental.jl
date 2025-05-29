```
RealInputToReactionOutput(components; initial_rates=nothing, name)
```

[`ReactionOutputPort`](@ref) に接続し、他方では [`ModelingToolkitStandardLibrary.Blocks.RealInput`s](@extref ModelingToolkitStandardLibrary.Blocks.RealInput) の一連に接続するシステムで、ModelingToolkitStandardLibrary との互換性を持ちます。このシステムは、対応するシンボル間の等価性を保証します。 [`ReactionOutputPort`](@ref) と同じ入力を受け取ります。

!!! info
    この関数は、[`ModelingToolkitStandardLibrary`](@extref ModelingToolkitStandardLibrary :doc:`index`) がロードされている必要があります。このライブラリでのみ有用です。


# コネクタ

  * `reactionoutput`: 接続する [`ReactionOutputPort`](@ref)
  * 各コンポーネントに対して1つの [`ModelingToolkitStandardLibrary.Blocks.RealInput`](@extref)
