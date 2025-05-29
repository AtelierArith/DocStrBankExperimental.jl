```
JarqueBeraTest(y::AbstractVector; adjusted::Bool=false)
```

When `adjusted` is `false`, compute the Jarque-Bera statistic to test the null hypothesis that a real-valued vector `y` is normally distributed.

Note that the approximation by the Chi-squared distribution does not work well and the speed of convergence is slow. In small samples, the test tends to be over-sized for nominal levels up to about 3% and under-sized for larger nominal levels (Mantalos, 2010).

When `adjusted` is `true`, compute the Adjusted Lagrangian Multiplier statistic to test the null hypothesis that a real-valued vector `y` is normally distributed.

Note that the use of Adjusted Lagrangian Multiplier is preferred over Jarque-Bera for small and medium sample sizes and it is a modification to the Jarque-Bera test (Urzua, 1996).

# References

  * Panagiotis Mantalos, 2011, "The three different measures of the sample skewness and kurtosis and the effects to the Jarque-Bera test for normality", International Journal of Computational Economics and Econometrics, Vol. 2, No. 1, [link](http://dx.doi.org/10.1504/IJCEE.2011.040576).
  * Carlos M. Urzúa, "On the correct use of omnibus tests for normality", Economics Letters, Volume 53, Issue 3, [link](https://doi.org/10.1016/S0165-1765(96)00923-8).

# External links

  * [Jarque-Bera test on Wikipedia](https://en.wikipedia.org/wiki/Jarque–Bera_test)
