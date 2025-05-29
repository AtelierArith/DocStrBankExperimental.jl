```
beta_inc(a, b, x, y=1-x)
```

Return a tuple $(I_{x}(a,b), 1-I_{x}(a,b))$ where $I_{x}(a,b)$ is the regularized incomplete beta function given by

$$
I_{x}(a,b) = \frac{1}{B(a,b)} \int_{0}^{x} t^{a-1}(1-t)^{b-1} \mathrm{d}t,
$$

where $B(a,b) = \Gamma(a)\Gamma(b)/\Gamma(a+b)$.

External links: [DLMF 8.17.1](https://dlmf.nist.gov/8.17.1), [Wikipedia](https://en.wikipedia.org/wiki/Beta_function#Incomplete_beta_function)

See also: [`beta_inc_inv`](@ref)
