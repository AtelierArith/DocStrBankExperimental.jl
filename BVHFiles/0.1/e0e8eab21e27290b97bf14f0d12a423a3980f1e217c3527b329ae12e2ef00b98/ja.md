```
change_sequence!(g::BVHGraph, v::Integer, sym::Symbol)
```

頂点 `v` の回転順序を `sym` に変更します。オイラー角はそれに応じて調整されます。

有効なシンボルは `:XYZ`, `:XYX`, `:XZX`, `:XZY`, `:YXZ`, `:YZX`, `:YXY`, `:YZY`,  `:ZXY`, `:ZYX`, `:ZXZ`, `:ZYZ` です。

参照: [`change_sequences!`](@ref)
