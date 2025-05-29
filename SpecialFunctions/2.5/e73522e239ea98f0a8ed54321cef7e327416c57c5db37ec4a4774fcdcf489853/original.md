```
besselhx(nu, [k=1,] z)
```

Compute the scaled Hankel function $\exp(∓iz) H_ν^{(k)}(z)$, where $k$ is 1 or 2, $H_ν^{(k)}(z)$ is `besselh(nu, k, z)`, and $∓$ is $-$ for $k=1$ and $+$ for $k=2$.  `k` defaults to 1 if it is omitted.

The reason for this function is that $H_ν^{(k)}(z)$ is asymptotically proportional to $\exp(∓iz)/\sqrt{z}$ for large $|z|$, and so the [`besselh`](@ref) function is susceptible to overflow or underflow when `z` has a large imaginary part.  The `besselhx` function cancels this exponential factor (analytically), so it avoids these problems.

External links: [DLMF 10.2](https://dlmf.nist.gov/10.2), [Wikipedia](https://en.wikipedia.org/wiki/Bessel_function#Hankel_functions:_H(1)%CE%B1,_H(2)%CE%B1)

See also: [`besselh`](@ref)
