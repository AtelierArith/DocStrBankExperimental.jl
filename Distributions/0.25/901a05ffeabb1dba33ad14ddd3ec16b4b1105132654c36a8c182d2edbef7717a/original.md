```
StudentizedRange(ν, k)
```

The *studentized range distribution* has probability density function:

$$
f(q; k, \nu) = \frac{\sqrt{2\pi}k(k - 1)\nu^{\nu/2}}{\Gamma{\left(\frac{\nu}{2}\right)}2^{\nu/2 - 1}} \int_{0}^{\infty} {x^{\nu}\phi(\sqrt{\nu}x)} \left[\int_{-\infty}^{\infty} {\phi(u)\phi(u - qx)[\Phi(u) - \Phi(u - qx)]^{k - 2}}du\right]dx
$$

where

$$
\begin{aligned}
\Phi(x) &= \frac{1 + erf(\frac{x}{\sqrt{2}})}{2} &&(\text{Normal Distribution CDF})\\
\phi(x) &= \Phi'(x) &&(\text{Normal Distribution PDF})
\end{aligned}
$$

```julia
StudentizedRange(ν, k)     # Studentized Range Distribution with parameters ν and k

params(d)        # Get the parameters, i.e. (ν, k)
```

External links

  * [Studentized range distribution on Wikipedia](http://en.wikipedia.org/wiki/Studentized_range_distribution)
