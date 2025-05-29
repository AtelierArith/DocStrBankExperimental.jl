```
diffusion_rate(results)
diffusion_rate(g, p, n; ...)
```

`diffusion`の出力結果または`diffusion`シミュレーション自体のパラメータを指定すると、(実行して)拡散率を返します。これは、指定された場合、`watch`に含まれる頂点の各シミュレーションステップで感染した累積頂点数を表すベクトルです。
