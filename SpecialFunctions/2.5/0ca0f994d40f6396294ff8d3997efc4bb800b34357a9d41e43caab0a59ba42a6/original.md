```
beta_inc_asymptotic_symmetric(a,b,lambda,epps)
```

Compute $I_{x}(a,b)$ using asymptotic expansion for `a, b >= 15`. It is assumed that $\lambda = (a+b)*y - b$.

External links: [DLMF 8.17.22](https://dlmf.nist.gov/8.17.22), [Wikipedia](https://en.wikipedia.org/wiki/Beta_function#Incomplete_beta_function)

See also: [`beta_inc`](@ref)

# Implementation

`BASYM(A,B,LAMBDA,EPS)` from [Didonato and Morris (1992)](@cite didonato_1992)
