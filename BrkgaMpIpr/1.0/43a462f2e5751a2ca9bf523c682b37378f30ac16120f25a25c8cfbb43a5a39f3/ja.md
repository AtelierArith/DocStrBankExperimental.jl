```
@enum BiasFunction
```

親を交配する際にバイアス関数を指定します。この関数は、元のBRKGAからの$\rho$（ロー）パラメータを置き換えます。与えられたランク$r$に対して、以下の関数があります：

  * `CONSTANT`: 交配のための親の数の逆数（すべての個体が同じ確率を持つ）
  * `CUBIC`: $r^{-3}$
  * `EXPONENTIAL`: $ϵ^{-r}$
  * `LINEAR`: $1 / r$
  * `LOGINVERSE`: $1 / \log(r + 1)$
  * `QUADRATIC`: $r^{-2}$
