```
map_exponents(f, m1::AbstractMonomialLike, m2::AbstractMonomialLike)
```

もし $m_1 = \prod x^{\alpha_i}$ かつ $m_2 = \prod x^{\beta_i}$ ならば、モノミアル $m = \prod x^{f(\alpha_i, \beta_i)}$ を返します。

### 例

乗算 `m1 * m2` は `map_exponents(+, m1, m2)` と同等であり、安全でない除算 `div_multiple(m1, m2)` は `map_exponents(-, m1, m2)` と同等です。`gcd(m1, m2)` は `map_exponents(min, m1, m2)` と同等であり、`lcm(m1, m2)` は `map_exponents(max, m1, m2)` と同等です。
