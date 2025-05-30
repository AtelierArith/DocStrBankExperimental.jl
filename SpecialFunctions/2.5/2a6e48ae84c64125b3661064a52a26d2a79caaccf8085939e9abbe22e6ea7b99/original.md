```
gamma_inc_cf(a, x, ind)
```

Computes $P(a,x)$ by continued fraction expansion given by:

$$
R(a,x) \cdot \cfrac{1}{1-\cfrac{z}{a+1+\cfrac{z}{a+2-\cfrac{(a+1)z}{a+3+\cfrac{2z}{a+4-\cfrac{(a+2)z}{a+5+\cfrac{3z}{a+6-\ddots}}}}}}}
$$

Used when `1 <= a <= BIG` and `x < x0`.

External links: [DLMF 8.9.2](https://dlmf.nist.gov/8.9.2)

See also: [`gamma_inc(a,x,ind)`](@ref SpecialFunctions.gamma_inc)
