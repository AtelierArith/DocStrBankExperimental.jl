```
total_outcomes(o::OutcomeSpace, x)
```

`est`の結果空間$\Omega$の長さ（基数）を返します。

一部の[`OutcomeSpace`](@ref)では、入力`x`の知識なしに基数が知られている場合、その場合は関数が`total_outcomes(est)`にディスパッチされます。一般的には、推定器に関係なく2引数バージョンを使用することが推奨されます。
