```
gamma_inc_taylor(a, x, ind)
```

Compute $P(a,x)$ using Taylor Series for P/R given by:

$$
R(a,x)/a * (1 + \sum_{n=1}^{\infty} x^{n}/((a+1)(a+2)...(a+n)))
$$

Used when `1 <= a <= BIG` and `x <= max{a, ln 10}`.

External links: [DLMF 8.11.2](https://dlmf.nist.gov/8.11.2)

See also: [`gamma_inc(a,x,ind)`](@ref SpecialFunctions.gamma_inc)
