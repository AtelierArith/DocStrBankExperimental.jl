```
gamma_inc(a,x,IND=0)
```

Returns a tuple $(p, q)$ where $p + q = 1$, and $p = P(a,x)$ is the Incomplete gamma function ratio given by:

$$
P(a,x) = \frac{1}{\Gamma (a)} \int_{0}^{x} e^{-t}t^{a-1} \mathrm{d}t.
$$

and $q = Q(a,x)$ is the Incomplete gamma function ratio given by:

$$
Q(a,x) = \frac{1}{\Gamma (a)} \int_{x}^{\infty} e^{-t}t^{a-1} \mathrm{d}t.
$$

In terms of these, the lower incomplete gamma function is $\gamma(a,x) = P(a,x) \Gamma(a)$ and the upper incomplete gamma function is $\Gamma(a,x) = Q(a,x) \Gamma(a)$.

`IND ∈ [0,1,2]` sets accuracy: `IND=0` means 14 significant digits accuracy, `IND=1` means 6 significant digit, and `IND=2` means only 3 digit accuracy.

External links: [DLMF 8.2.4](https://dlmf.nist.gov/8.2.4), [Wikipedia](https://en.wikipedia.org/wiki/Incomplete_gamma_function)

See also [`gamma(z)`](@ref SpecialFunctions.gamma), [`gamma_inc_inv(a,p,q)`](@ref SpecialFunctions.gamma_inc_inv)
