```
siegel_reduction(tau::AcbMatrix) -> AcbMatrix
```

周期行列 tau のシーゲル還元を計算します。すなわち、siegel*reduction(tau) = X +iY と書きます。すべての n, m に対して |X*mn| <= 1/2 となり、Y によって生成される格子の最短ベクトルの二乗長は sqrt(3)/2 より小さくなります。
