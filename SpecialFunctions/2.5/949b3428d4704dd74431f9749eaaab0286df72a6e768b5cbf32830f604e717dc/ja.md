```
gamma(a,x)
```

上側不完全ガンマ関数を返します

$$
\Gamma(a,x) = \int_x^\infty t^{a-1} e^{-t} \mathrm{d}t
$$

任意の実数または複素数の `a` と `x` をサポートします。

（通常のガンマ関数 [`gamma(x)`](@ref) は $\Gamma(a) = \Gamma(a,0)$ に対応します。上側および下側（$\gamma(a,x)$）の不完全ガンマ関数を $\Gamma(a)$ でスケーリングして計算する [`gamma_inc`](@ref) 関数も参照してください。

外部リンク: [DLMF 8.2.2](https://dlmf.nist.gov/8.2.2), [Wikipedia](https://en.wikipedia.org/wiki/Incomplete_gamma_function)
