```
beta_inc_power_series(a, b, x, epps)
```

Computes $I_x(a,b)$ using power series:

$$
I_{x}(a,b) = G(a,b) x^{a}/a \left[1 + a \sum_{j=1}^{\infty} ((1-b)(2-b)\dots(j-b)/j!(a+j)) x^{j}\right]
$$

External links: [DLMF 8.17.22](https://dlmf.nist.gov/8.17.22), [Wikipedia](https://en.wikipedia.org/wiki/Beta_function#Incomplete_beta_function)

See also: [`beta_inc`](@ref)

# Implementation

`BPSER(A,B,X,EPS)` from [Didonato and Morris (1992)](@cite didonato_1992)
