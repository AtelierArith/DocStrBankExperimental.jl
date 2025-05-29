```
diffusion_rate(results)
diffusion_rate(g, p, n; ...)
```

`diffusion`の出力結果または`diffusion`シミュレーション自体のパラメータを指定すると、（実行して）指定された場合は`watch`に含まれる頂点に制限された各シミュレーションステップで感染した頂点の累積数を表すベクトルとして拡散率を返します。
