```
reflect(M, p, x, kwargs...)
reflect!(M, q, p, x, kwargs...)
```

多様体 `M` の点 `p` で点 `x` を反射するには、次のようにします。

$$
\operatorname{refl}_p(q) = \operatorname{retr}_p(-\operatorname{retr}^{-1}_p q),
$$

ここで、$\operatorname{retr}$ と $\operatorname{retr}^{-1}$ はそれぞれ引き戻しと逆引き戻しを示します。

これは `q` のインプレースでも行うことができます。

## キーワード引数

  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する引き戻し $\operatorname{retr}$、[引き戻しに関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照してください。
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する逆引き戻し $\operatorname{retr}^{-1}$、[引き戻しとその逆に関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照してください。

さらに `reflect!` には

  * `X=zero_vector(M,p)`: インプレースで逆引き戻しを計算するための一時メモリ。そうでなければ、これは元々割り当てられるメモリです。
