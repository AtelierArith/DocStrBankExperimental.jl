```
beta_inc(a, b, x, y=1-x)
```

タプル $(I_{x}(a,b), 1-I_{x}(a,b))$ を返します。ここで $I_{x}(a,b)$ は次のように定義される正規化不完全ベータ関数です。

$$
I_{x}(a,b) = \frac{1}{B(a,b)} \int_{0}^{x} t^{a-1}(1-t)^{b-1} \mathrm{d}t,
$$

ここで $B(a,b) = \Gamma(a)\Gamma(b)/\Gamma(a+b)$ です。

外部リンク: [DLMF 8.17.1](https://dlmf.nist.gov/8.17.1), [Wikipedia](https://en.wikipedia.org/wiki/Beta_function#Incomplete_beta_function)

関連: [`beta_inc_inv`](@ref)
