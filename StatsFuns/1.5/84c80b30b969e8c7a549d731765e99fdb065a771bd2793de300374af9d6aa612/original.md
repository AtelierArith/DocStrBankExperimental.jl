```
lstirling_asym(x)
```

The remainder term after [Stirling's approximation](https://en.wikipedia.org/wiki/Stirling%27s_approximation) to [`loggamma`](@ref):

$$
\log \Gamma(x) \approx x \log(x) - x + \log(2\pi/x)/2 = \log(x)*(x-1/2) + \log(2\pi)/2 - x
$$

In Julia syntax, this means:

```
lstirling_asym(x) = loggamma(x) + x - (x-0.5)*log(x) - 0.5*log(2π)
```

For sufficiently large `x`, this can be approximated using the asymptotic *Stirling's series* ([DLMF 5.11.1](https://dlmf.nist.gov/5.11.1)):

$$
\frac{1}{12x} - \frac{1}{360x^3} + \frac{1}{1260x^5} - \frac{1}{1680x^7} + \ldots
$$

The truncation error is bounded by the first omitted term, and is of the same sign.

Relative error of approximation is bounded by     (174611/125400 x^-19) / (1/12 x^-1 - 1/360 x^-3) which is < 1/2 ulp for x >= 10.0, and total numeric error appears to be < 2 ulps

# References

  * Temme, N. (1996) Special functions: An introduction to the classical functions of  mathematical physics, Wiley, New York, ISBN: 0-471-11313-1, Chapter 3.6, pp 61-65.
  * Weisstein, Eric W. ["Stirling's Series."](http://mathworld.wolfram.com/StirlingsSeries.html). MathWorld.
  * [OEIS A046968](http://oeis.org/A046968) and [OEIS A046969](http://oeis.org/A046969) for the series coefficients
