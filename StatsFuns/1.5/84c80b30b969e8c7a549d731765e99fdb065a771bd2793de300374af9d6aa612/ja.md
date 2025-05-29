```
lstirling_asym(x)
```

[スターリングの近似](https://en.wikipedia.org/wiki/Stirling%27s_approximation)における残差項は[`loggamma`](@ref):

$$
\log \Gamma(x) \approx x \log(x) - x + \log(2\pi/x)/2 = \log(x)*(x-1/2) + \log(2\pi)/2 - x
$$

Juliaの構文では、これは次のように表されます:

```
lstirling_asym(x) = loggamma(x) + x - (x-0.5)*log(x) - 0.5*log(2π)
```

十分に大きな`x`に対して、これは漸近的な*スターリング級数*を用いて近似できます（[DLMF 5.11.1](https://dlmf.nist.gov/5.11.1)）:

$$
\frac{1}{12x} - \frac{1}{360x^3} + \frac{1}{1260x^5} - \frac{1}{1680x^7} + \ldots
$$

切り捨て誤差は最初に省略された項によって制約され、同じ符号を持ちます。

近似の相対誤差は(174611/125400 x^-19) / (1/12 x^-1 - 1/360 x^-3)によって制約され、これはx >= 10.0のときに< 1/2 ulpであり、総数値誤差は< 2 ulpsであるようです。

# 参考文献

  * Temme, N. (1996) Special functions: An introduction to the classical functions of  mathematical physics, Wiley, New York, ISBN: 0-471-11313-1, Chapter 3.6, pp 61-65.
  * Weisstein, Eric W. ["Stirling's Series."](http://mathworld.wolfram.com/StirlingsSeries.html). MathWorld.
  * [OEIS A046968](http://oeis.org/A046968) および [OEIS A046969](http://oeis.org/A046969) の系列係数
