```
beta_inc_cont_fraction(a,b,x,y,lambda,epps)
```

Compute $I_{x}(a,b)$ using continued fraction expansion when `a, b > 1`. It is assumed that $\lambda = (a+b)*y - b$

External links: [DLMF 8.17.22](https://dlmf.nist.gov/8.17.22), [Wikipedia](https://en.wikipedia.org/wiki/Beta_function#Incomplete_beta_function)

See also: [`beta_inc`](@ref)

# Implementation

`BFRAC(A,B,X,Y,LAMBDA,EPS)` from [Didonato and Morris (1992)](@cite didonato_1992)
