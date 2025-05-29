```
phi(A,k[;cache]) -> [phi_0(A),phi_1(A),...,phi_k(A)]
```

行列の phi 関数をすべての次数 k まで計算します。 `k` >= 1。

phi 関数は次のように定義されます。

$$
\varphi_0(z) = \exp(z),\quad \varphi_{k+1}(z) = \frac{\varphi_k(z) - 1}{z}
$$

各基底ベクトルに対して `phiv_dense` を呼び出して答えを得ます。もし A が `Diagonal` の場合、各対角要素にスカラー `phi` を呼び出し、返される値も `Diagonal` になります。
