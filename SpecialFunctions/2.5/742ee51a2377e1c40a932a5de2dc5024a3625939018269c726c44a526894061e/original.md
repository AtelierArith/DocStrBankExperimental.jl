```
sinint(x)
```

Compute the sine integral function of $x$, defined by

$$
\operatorname{Si}(x)
:= \int_0^x \frac{\sin t}{t} \, \mathrm{d}t
\quad \text{for} \quad
x \in \mathbb{R} \,.
$$

External links: [DLMF 6.2.9](https://dlmf.nist.gov/6.2.9), [Wikipedia](https://en.wikipedia.org/wiki/Trigonometric_integral#Sine_integral).

See also: [`cosint(x)`](@ref SpecialFunctions.cosint).

# Implementation

Using the rational approximants tabulated in:

> A.J. MacLeod, "Rational approximations, software and test methods for sine and cosine integrals", Numer. Algor. 12, pp. 259–272 (1996). [https://doi.org/10.1007/BF02142806](https://doi.org/10.1007/BF02142806), [https://link.springer.com/article/10.1007/BF02142806](https://link.springer.com/article/10.1007/BF02142806).


Note: the second zero of $\text{Ci}(x)$ has a typo that is fixed: $r_1 = 3.38418 0422\mathbf{8} 51186 42639 78511 46402$ in the article, but is in fact: $r_1 = 3.38418 0422\mathbf{5} 51186 42639 78511 46402$.
