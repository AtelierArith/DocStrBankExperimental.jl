```
Quadratic(Q, q; iterative=false)
```

行列 `Q`（密または疎、対称かつ正定値）とベクトル `q` に対して、二次関数を返します。

$$
f(x) = \tfrac{1}{2}\langle Qx, x\rangle + \langle q, x \rangle.
$$

デフォルトでは、`prox!` を評価するために直接法（コレスキー分解に基づく）が使用されます。`iterative=true` の場合、`prox!` は反復法を使用して近似的に評価されます。
