```
MeroQuadGKJL(; order = 7, norm = norm, rho = 1.0, rootmeth = IteratedIntegration.MeroQuadGK.NewtonDeflation())
```

スカラーの複素値被積分関数に対する1次元極点除去数値積分法です。実軸上では通常の`quadgk`の動作がデフォルトですが、標準区間`[-1,1]`のベルンシュタイン楕円の意味で1/fの近くの根を見つけた場合、その区間で極点除去を試みます。
