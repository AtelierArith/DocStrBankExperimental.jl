```
Rval = evalfr(R; fval = 0)
```

連続時間システムの場合、`λ = val` のときの有理伝達関数行列 `R(λ)` を評価します。ここで、`val = im*fval` です。離散時間システムの場合は、`val = exp(im*fval*abs(Ts))` であり、`Ts` はシステムのサンプリング時間です。
