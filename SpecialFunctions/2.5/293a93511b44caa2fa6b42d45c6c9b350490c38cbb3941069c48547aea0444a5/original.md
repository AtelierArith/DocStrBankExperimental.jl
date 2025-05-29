```
besselh(nu, [k=1,] x)
```

Bessel function of the third kind of order `nu` (the Hankel function). `k` is either 1 or 2, selecting [`hankelh1`](@ref) or [`hankelh2`](@ref), respectively. `k` defaults to 1 if it is omitted.

External links: [DLMF 10.2.5](https://dlmf.nist.gov/10.2.5) and [DLMF 10.2.6](https://dlmf.nist.gov/10.2.6), [Wikipedia](https://en.wikipedia.org/wiki/Bessel_function#Hankel_functions:_H(1)%CE%B1,_H(2)%CE%B1)

See also: [`besselhx`](@ref) for an exponentially scaled variant.
