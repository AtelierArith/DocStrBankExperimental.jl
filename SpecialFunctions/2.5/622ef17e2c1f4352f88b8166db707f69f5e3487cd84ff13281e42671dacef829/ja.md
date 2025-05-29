```
loggamma(a,x)
```

上側不完全ガンマ関数 [`gamma(a,x)`](@ref) の対数を返します：

$$
\log \Gamma(a,x) = \log \int_x^\infty t^{a-1} e^{-t} \mathrm{d}t
$$

任意の実数または複素数 `a` と `x` をサポートします。

`a` および/または `x` が複素数の場合、`exp(loggamma(a,x))` は `gamma(a,x)` と一致します（浮動小数点誤差を除く）が、`loggamma(a,x)` は `log(gamma(a,x))` と $2\pi i$ の整数倍だけ異なる場合があります（つまり、異なる分岐切断を使用する可能性があります）。

また [`loggamma(x)`](@ref) も参照してください。
