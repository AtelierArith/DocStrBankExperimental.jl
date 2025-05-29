```
reflect(M, p, x, kwargs...)
reflect!(M, q, p, x, kwargs...)
```

多様体 `M` の点 `p` で点 `x` を反射するには、次のようにします。

$$
    \operatorname{refl}_p(x) = \operatorname{retr}_p(-\operatorname{retr}^{-1}_p x).
$$

ここで、$\operatorname{retr}$ と $\operatorname{retr}^{-1}$ はそれぞれリトラクションと逆リトラクションを示します。これは `q` の代わりに行うこともできます。

## キーワード引数

  * `retraction_method`:         （`default_retraction_metiod(M, typeof(p))`）反射に使用するリトラクション
  * `inverse_retraction_method`: （`default_inverse_retraction_method(M, typeof(p))`）反射内で使用する逆リトラクション

さらに `reflect!` には

  * `X`:                         （`zero_vector(M,p)`）逆リトラクションを計算するための一時メモリ。そうでなければ、これは元々割り当てられるメモリです。

```
