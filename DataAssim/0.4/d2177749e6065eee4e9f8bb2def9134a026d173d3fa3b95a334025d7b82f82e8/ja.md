```
x,P = KalmanFilter(xi,Pi,ℳ,Q,yo,R,𝓗,nmax,no)
```

モデル `ℳ` と `nmax` タイムステップを持つカルマンフィルタで、初期条件 `xi` と誤差共分散 `Pi` から始まります。観測 `yo`（および誤差共分散 `R`）は、`no` で与えられたタイムステップで観測オペレーター `H` を用いて同化されます。
