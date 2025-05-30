```
cosint(x)
```

Compute the cosine integral function of $x$, defined by

$$
\operatorname{Ci}(x)
:= \gamma + \log x + \int_0^x \frac{\cos (t) - 1}{t} \, \mathrm{d}t
\quad \text{for} \quad
x > 0 \,,
$$

where $\gamma$ is the Euler-Mascheroni constant.

External links: [DLMF 6.2.13](https://dlmf.nist.gov/6.2.13), [Wikipedia](https://en.wikipedia.org/wiki/Trigonometric_integral#Cosine_integral).

See also: [`sinint(x)`](@ref SpecialFunctions.sinint).

# Implementation

Using the rational approximants tabulated in [MacLeod (1996)](@cite macleod_1996).

Note: the second zero of $\text{Ci}(x)$ has a typo that is fixed: $r_1 = 3.38418 0422\mathbf{8} 51186 42639 78511 46402$ in the article, but is in fact: $r_1 = 3.38418 0422\mathbf{5} 51186 42639 78511 46402$.
