`DIVIDEPLATEAUS!` - 高さの最も急なグラフにおける高原を分割する

```
 divideplateaus!(sag)
```

  * `sag`: 高さの最も急なグラフ（有向かつ無重み）。 `sag[x,y,z]` は (x,y,z) から出る辺をエンコードした6ビットの数を含みます。

高さの最も急なグラフを次のように修正します。

1. 非最大の高原をできるだけ早く出口に向かうパスに分割する
2. 複数の出力辺の間での引き分けを解消する

これは `sag` のインプレース修正です。
