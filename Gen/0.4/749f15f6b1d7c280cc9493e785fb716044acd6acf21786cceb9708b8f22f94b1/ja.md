```
(choices, weight, retval) = propose(gen_fn::GenerativeFunction, args::Tuple)
```

サンプリングされた割り当てを行い、その割り当てを提案する確率を計算します。

引数（`args`）に基づいて、$t \sim p(\cdot; x)$ と $r \sim p(\cdot; x, t)$ をサンプリングし、$t$（`choices`）と重み（`weight`）を返します：

$$
\log \frac{p(r, t; x)}{q(r; x, t)}
$$
