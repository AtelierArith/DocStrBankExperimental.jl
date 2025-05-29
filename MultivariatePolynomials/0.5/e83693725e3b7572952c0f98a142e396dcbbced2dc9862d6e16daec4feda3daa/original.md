```
map_exponents(f, m1::AbstractMonomialLike, m2::AbstractMonomialLike)
```

If $m_1 = \prod x^{\alpha_i}$ and $m_2 = \prod x^{\beta_i}$ then it returns the monomial $m = \prod x^{f(\alpha_i, \beta_i)}$.

### Examples

The multiplication `m1 * m2` is equivalent to `map_exponents(+, m1, m2)`, the unsafe division `div_multiple(m1, m2)` is equivalent to `map_exponents(-, m1, m2)`, `gcd(m1, m2)` is equivalent to `map_exponents(min, m1, m2)`, `lcm(m1, m2)` is equivalent to `map_exponents(max, m1, m2)`.
