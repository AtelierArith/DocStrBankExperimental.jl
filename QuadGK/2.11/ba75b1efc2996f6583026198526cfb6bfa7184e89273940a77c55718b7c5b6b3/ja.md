```
quadgk_segbuf_print(args...; kws...)
```

`quadgk_print(args...; kws...)` と同じですが、タプル `(I, E, segbuf, count)` を返します。ここで `segbuf` はセグメントバッファ（最終的な積分評価に使用される部分区間を格納）であり、後続の `quadgk` および関連関数への呼び出しで `segbuf` および/または `eval_segbuf` 引数として渡すことができます。
