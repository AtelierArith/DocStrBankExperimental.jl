```
gamma_inc_inv_alarge(a, minpq, pcase)
```

`a` が大きいときの初期近似 `x0` を計算します。逆問題は次のように書き換えられます：

$$
0.5 \operatorname{erfc}(\eta \sqrt{a/2}) + R_{a}(\eta) = q
$$

`a` の大きな値に対して、次のように書くことができます：$\eta(q,a) = \eta_{0}(q,a) + \epsilon(\eta_{0},a)$ そして展開することが可能です：

$$
\epsilon(\eta_{0},a) = \epsilon_{1}(\eta_{0},a)/a + \epsilon_{2}(\eta_{0},a)/a^{2} + \epsilon_{3}(\eta_{0},a)/a^{3} + \cdots
$$

これは以下の [`coeff1`](@ref), [`coeff2`](@ref) および [`coeff3`](@ref) 関数によって計算されます。これはタプル `(x0,fp)` を返し、`fp` は元の冪級数を逆転させた後の係数の近似として計算されます。
