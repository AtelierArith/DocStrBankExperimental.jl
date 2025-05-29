```
SplinedBody(x,y,Δx[,closuretype=ClosedBody]) -> BasicBody
```

制御点 `x` と `y` を使用して、制御点を通過する曲線上に均等に間隔を空けた点のセットを作成します（間隔は `Δx`）。三次パラメトリックスプラインアルゴリズムが使用されます。オプションのパラメータ `closuretype` が `OpenBody` に設定されている場合、端点は結合されません。
