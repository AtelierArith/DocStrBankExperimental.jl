```
rval = evalfr(r; fval = 0)
```

連続時間システムの場合、`λ = val` の有理伝達関数 `r(λ)` を評価します。ここで、`val = im*fval` です。離散時間システムの場合は、`val = exp(im*fval*Ts)` であり、`Ts` はシステムのサンプリング時間です。
