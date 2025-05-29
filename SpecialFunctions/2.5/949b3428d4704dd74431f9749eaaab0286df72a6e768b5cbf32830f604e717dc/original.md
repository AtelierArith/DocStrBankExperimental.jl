```
gamma(a,x)
```

Returns the upper incomplete gamma function

$$
\Gamma(a,x) = \int_x^\infty t^{a-1} e^{-t} \mathrm{d}t
$$

supporting arbitrary real or complex `a` and `x`.

(The ordinary gamma function [`gamma(x)`](@ref) corresponds to $\Gamma(a) = \Gamma(a,0)$. See also the [`gamma_inc`](@ref) function to compute both the upper and lower ($\gamma(a,x)$) incomplete gamma functions scaled by $\Gamma(a)$.

External links: [DLMF 8.2.2](https://dlmf.nist.gov/8.2.2), [Wikipedia](https://en.wikipedia.org/wiki/Incomplete_gamma_function)
