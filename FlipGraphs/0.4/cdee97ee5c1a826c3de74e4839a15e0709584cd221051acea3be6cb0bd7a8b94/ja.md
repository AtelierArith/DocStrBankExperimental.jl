```
is_flippable(D::DeltaComplex, e::Integer) :: Bool
```

与えられたエッジがフリップ可能であれば `true` を返します。

このエッジが `TriFace` 自身に接続していない場合は、常にそうなります。
