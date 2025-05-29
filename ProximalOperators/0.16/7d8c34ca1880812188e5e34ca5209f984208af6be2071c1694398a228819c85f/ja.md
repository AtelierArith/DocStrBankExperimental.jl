```
LeastSquares(A, b, λ=1.0; iterative=false)
```

行列 `A`、ベクトル `b` およびスカラー `λ` に対して、次の関数を返します。

$$
f(x) = \tfrac{\lambda}{2}\|Ax - b\|^2.
$$

デフォルトでは、`prox!` を評価するために直接法（コレスキー分解に基づく）が使用されます。`iterative=true` の場合、`prox!` は反復法を使用して近似的に評価されます。
