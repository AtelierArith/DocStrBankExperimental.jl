```
prox(f, x, gamma=1)
```

関数 `f` の近接写像を `x` で評価し、ステップサイズ `gamma` を使用します。

近接写像は次のように定義されます。

$$
\mathrm{prox}_{\gamma f}(x) = \arg\min_z \left\{ f(z) + \tfrac{1}{2\gamma}\|z-x\|^2 \right\}.
$$

戻り値はタプル `(y, fy)` で、次の要素から構成されます。

  * `y`: ステップサイズ `gamma` で `x` における `f` の近接写像の出力
  * `fy`: `y` における `f` の値

詳細については、[`prox!`](@ref) を参照してください。
