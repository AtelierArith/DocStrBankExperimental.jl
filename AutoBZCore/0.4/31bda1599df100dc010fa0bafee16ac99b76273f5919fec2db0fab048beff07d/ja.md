```
ContQuadGKJL(; order = 7, norm = norm, rho = 1.0, rootmeth = IteratedIntegration.ContQuadGK.NewtonDeflation())
```

スカラーの複素値被積分関数に対する1次元輪郭変形数値積分スキームです。実軸上では通常の`quadgk`の動作がデフォルトですが、標準セグメント`[-1,1]`のベルンシュタイン楕円の意味で近くに1/fの根を見つけた場合、上半平面または下半平面のいずれかで、推定される極から輪郭を凹ませます。
