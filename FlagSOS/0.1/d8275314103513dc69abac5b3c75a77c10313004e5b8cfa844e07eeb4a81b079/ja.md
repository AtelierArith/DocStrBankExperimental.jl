```
FlagModel{T <: Flag, N, D} <: AbstractFlagModel{T, N, D}
```

内部Flag型'T'を持つFlagモデル。

# パラメータ

  * `T`: 対象Flag型
  * `N`: 制限パラメータ、`AbstractFlagModel`を参照
  * `D`: 最終最適化問題の係数のデータ型
