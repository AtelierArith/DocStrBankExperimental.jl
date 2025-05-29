```
LowRankFun(f, space::TensorSpace)
```

二変数関数を低ランク形式で近似します

$$
f(x,y) = \sum_i \sigma_i \phi_i(x) \psi_i(y)
$$

ここで、$\sigma_i$ は最大特異値を表し、$\phi_i(x)$ と $\psi_i(y)$ は直交基底です。合計は、許容可能な誤差が達成されるまで切り捨てられます。

# 例

```jldoctest
julia> f = (x,y) -> x^2 * y^3;

julia> L = LowRankFun(f, Chebyshev() ⊗ Chebyshev());

julia> L(0.1, 0.2) ≈ f(0.1, 0.2)
true
```
