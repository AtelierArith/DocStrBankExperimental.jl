```
embed_graph([mode,] g::SimpleGraph; vertex_order=MinhThiTrick())
```

グラフ `g` を単位円盤グリッドに埋め込みます。オプションの引数 `mode` は `Weighted()` または `UnWeighted` にすることができます。`vertex_order` はベクトルまたは以下のいずれかの入力にすることができます。

```
* `Greedy()` は高速ですが最適ではありません。
* `MinhThiTrick()` は遅いですが最適です。
```
