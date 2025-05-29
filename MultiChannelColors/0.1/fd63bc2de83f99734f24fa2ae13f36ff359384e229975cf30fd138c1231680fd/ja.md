```
MultiChannelColor(i₁, i₂, ...)
MultiChannelColor((i₁, i₂, ...))
MultiChannelColor{T}(...)                # 要素型 T に強制変換
```

標準の色空間への `convert` メソッドを欠くマルチチャネル「生」色を表します。もし `c` が `MultiChannelColor` オブジェクトであれば、`Tuple(c)` は強度のタプル（チャネルごとに1つ）です。

[`ColorMixture`](@ref) は、RGB への組み込み変換を持つ代替手段です。
