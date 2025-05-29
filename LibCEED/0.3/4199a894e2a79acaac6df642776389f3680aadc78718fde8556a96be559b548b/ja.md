```
lobatto_quadrature(q, mode::Mode=Abscissa)
```

`q` 点のガウス・ロバット数値積分法を返します（次数 $2q-3$ の多項式を正確に積分します）。

`mode` が `AbscissaAndWeights` の場合、重みとアブシッサの両方がタプル `(x,w)` として返されます。

そうでない場合（`mode` が `Abscissa` の場合）、アブシッサ `x` のみが返されます。
