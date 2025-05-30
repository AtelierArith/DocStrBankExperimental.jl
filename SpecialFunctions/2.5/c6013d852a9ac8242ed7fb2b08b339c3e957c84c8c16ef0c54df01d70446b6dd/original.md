```
gamma_inc_inv_alarge(a, minpq, pcase)
```

Compute `x0` - initial approximation when `a` is large. The inversion problem is rewritten as:

$$
0.5 \operatorname{erfc}(\eta \sqrt{a/2}) + R_{a}(\eta) = q
$$

For large values of `a` we can write: $\eta(q,a) = \eta_{0}(q,a) + \epsilon(\eta_{0},a)$ and it is possible to expand:

$$
\epsilon(\eta_{0},a) = \epsilon_{1}(\eta_{0},a)/a + \epsilon_{2}(\eta_{0},a)/a^{2} + \epsilon_{3}(\eta_{0},a)/a^{3} + \cdots
$$

which is calculated by [`coeff1`](@ref), [`coeff2`](@ref) and [`coeff3`](@ref) functions below. This returns a tuple `(x0,fp)`, where `fp` is computed since it's an approximation for the coefficient after inverting the original power series.
