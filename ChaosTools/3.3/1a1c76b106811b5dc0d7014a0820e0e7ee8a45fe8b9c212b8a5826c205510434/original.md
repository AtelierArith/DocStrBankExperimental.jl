```
testchaos01(x::Vector [, cs, N0]) -> chaotic?
```

Perform the so called "0-1" test for chaos introduced by Gottwald and Melbourne[^Gottwald2016] on the timeseries `x`. Return `true` if `x` is chaotic, `false` otherwise.

## Description

This method tests if the given timeseries is chaotic or not by transforming it into a two-dimensional diffusive process like so:

$$
p_n = \sum_{j=1}^{n}\phi_j \cos(j c),\quad q_n = \sum_{j=1}^{n}\phi_j \sin(j c)
$$

If the timeseries is chaotic, the mean square displacement of the process grows as `sqrt(length(x))`, while it stays constant if the timeseries is regular.

The implementation here computes `K`, a coefficient measuring the growth of the mean square displacement, and simply checks if `K > 0.5`. `K` is the median of $K_c$ over given `c`, see the reference.

If you want to access the various `Kc` you should call the method `testchaos01(x, c::Real, N0)` which returns `Kc`. In fact, the high level method is just `median(testchaos01(x, c, N0) for c in cs) > 0.5`.

`cs` defaults to `3π/5*rand(100) + π/4` and `N0`, the length of the two-dimensional process, is `N0 = length(x)/10`.

For data sampled from continuous dynamical systems, some care must be taken regarding the values of `cs`. Also note that this method performs rather poorly with even the slight amount of noise, returning `true` for even small amounts of noise noisy timeseries. Some possibilities to alleviate this exist, but are context specific on the application. See [^Gottwald2016] for more info.

[^Gottwald2016]: Gottwald & Melbourne, “The 0-1 test for chaos: A review” [Lect. Notes Phys., vol. 915, pp. 221–247, 2016.]( www.doi.org/10.1007/978-3-662-48410-4_7)
