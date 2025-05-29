```
DimMover(from, to)
```

次元ムーバーレイヤーを構築します。

各時点がチャネルであることを考慮して、Neural DEの出力のバッチインデックスと時間インデックスを入れ替えるために、`AbstractLuxLayer`の最後のレイヤーとして使用することで、Luxの従来の順序`(data, channel, batch)`を持つことができます。
