```
change_sequences!(g::BVHGraph, sym::Symbol)
```

すべての頂点の回転順序を `sym` に変更します。オイラー角はそれに応じて調整されます。

有効なシンボルは `:XYZ`, `:XYX`, `:XZX`, `:XZY`, `:YXZ`, `:YZX`, `:YXY`, `:YZY`,  `:ZXY`, `:ZYX`, `:ZXZ`, `:ZYZ` です。

参照: [`change_sequence!`](@ref)
