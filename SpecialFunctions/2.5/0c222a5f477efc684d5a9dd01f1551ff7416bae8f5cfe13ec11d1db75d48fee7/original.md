```
gamma_inc_asym(a, x, ind)
```

Compute $P(a,x)$ using asymptotic expansion given by:

$$
R(a,x)/a * (1 + \sum_{n=1}^{N-1}(a_{n}/x^{n} + \Theta _{n}a_{n}/x^{n}))
$$

where `R(a,x) = rgammax(a,x)`. Used when `1 <= a <= BIG` and `x >= x0`.

External links: [DLMF 8.11.2](https://dlmf.nist.gov/8.11.2)

See also: [`gamma_inc(a,x,ind)`](@ref SpecialFunctions.gamma_inc)
