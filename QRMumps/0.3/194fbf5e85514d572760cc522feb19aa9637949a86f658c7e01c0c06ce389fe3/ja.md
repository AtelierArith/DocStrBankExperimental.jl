```
qrm_residual_norm!(spmat, b, x, nrm; transp='n')
```

この関数は、残差のスケーリングされたノルム $\frac{\|b - Ax\|_{\infty}}{\|b\|_{\infty} + \|x\|_{\infty} \|A\|_{\infty}}$ を計算します。すなわち、ノルムに基づく後方誤差です。

#### 入力引数 :

  * `spmat`: 入力行列。
  * `b`: 右辺。
  * `x`: 解ベクトル。
  * `nrm`: 計算されたノルム。
  * `transp`: A, Aᵀ または Aᴴ を使用するかどうか。`'t'`、`'c'` または `'n'` のいずれかです。
