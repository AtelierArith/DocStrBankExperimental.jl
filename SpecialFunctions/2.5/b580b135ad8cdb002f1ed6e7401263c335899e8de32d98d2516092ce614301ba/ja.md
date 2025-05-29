```
gamma_inc(a,x,IND=0)
```

タプル $(p, q)$ を返します。ここで $p + q = 1$ であり、$p = P(a,x)$ は不完全ガンマ関数比で次のように定義されます：

$$
P(a,x) = \frac{1}{\Gamma (a)} \int_{0}^{x} e^{-t}t^{a-1} \mathrm{d}t.
$$

また、$q = Q(a,x)$ は不完全ガンマ関数比で次のように定義されます：

$$
Q(a,x) = \frac{1}{\Gamma (a)} \int_{x}^{\infty} e^{-t}t^{a-1} \mathrm{d}t.
$$

これらに基づいて、下側不完全ガンマ関数は $\gamma(a,x) = P(a,x) \Gamma(a)$ であり、上側不完全ガンマ関数は $\Gamma(a,x) = Q(a,x) \Gamma(a)$ です。

`IND ∈ [0,1,2]` は精度を設定します：`IND=0` は14桁の有効数字の精度を意味し、`IND=1` は6桁の有効数字、`IND=2` は3桁の精度のみを意味します。

外部リンク: [DLMF 8.2.4](https://dlmf.nist.gov/8.2.4), [Wikipedia](https://en.wikipedia.org/wiki/Incomplete_gamma_function)

関連項目として [`gamma(z)`](@ref SpecialFunctions.gamma), [`gamma_inc_inv(a,p,q)`](@ref SpecialFunctions.gamma_inc_inv) を参照してください。
