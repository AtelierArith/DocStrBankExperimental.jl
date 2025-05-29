```
empiricalloglikelihood(x, xgen)
empiricalloglikelihood(bm, x, nparticles)
empiricalloglikelihood(bm, x, nparticles, burnin)
```

データセット `x` の平均経験的対数尤度を計算します。サンプルの確率は、モデルによって生成されたデータセットにおけるサンプルの経験的確率として推定されます。このデータセットは `xgen` として与えることができるか、ボルツマンマシン `bm` で `burnin` ステップ（デフォルトは5）で `nparticles` を使用してギブスサンプラーを実行することによって生成されます。`x` のサンプルが生成されたデータセットに含まれていない場合、エラーが発生します。
