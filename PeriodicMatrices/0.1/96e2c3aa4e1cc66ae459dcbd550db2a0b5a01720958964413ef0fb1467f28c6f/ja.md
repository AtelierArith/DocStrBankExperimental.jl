```
 ffm2psm(Af::FourierFunctionMatrix, nrange atol = 0, rtol = 10*n*ϵ,) -> A::Matrix{Num}
```

フーリエ関数行列 `Af` の調和成分の範囲 `nrange` を記号行列 `A` に変換します。デフォルトの範囲は `nrange = 0:n` で、ここで `n` は最大調和数の次数です。非ゼロ係数を評価するために使用される許容誤差は `tol = max(atol, rtol*maxnorm)` であり、ここで `maxnorm` は `Af(t)` の係数 `ac_i` と `as_i` の最大絶対値です。許容誤差のデフォルト値は `atol = 0` および `rtol = 10*n*ϵ` で、ここで `ϵ` は作業用の機械精度です。
