```
loggamma(x)
```

与えられた `x` の [`gamma`](@ref) の対数を計算します。`x` が `Real` の場合、`gamma(x)` が負であれば `DomainError` をスローします。

`x` が複素数の場合、`exp(loggamma(x))` は `gamma(x)` に一致します（浮動小数点誤差を除く）が、`loggamma(x)` は `log(gamma(x))` と $2πi$ の整数倍だけ異なる場合があります（すなわち、異なるブランチカットを使用する可能性があります）。

実数 `x` のための [`logabsgamma`](@ref) も参照してください。
