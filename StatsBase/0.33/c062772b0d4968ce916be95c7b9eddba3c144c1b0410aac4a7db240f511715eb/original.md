```
cumulant(v, k, [wv::AbstractWeights], m=mean(v))
```

Return the `k`th order cumulant of a real-valued array `v`, optionally specifying a weighting vector `wv` and a pre-computed mean `m`.

If `k` is a range of `Integer`s, then return all the cumulants of orders in this range as a vector.

This quantity is calculated using a recursive definition on lower-order cumulants and central moments.

Reference: Smith, P. J. 1995. A Recursive Formulation of the Old Problem of Obtaining Moments from Cumulants and Vice Versa. The American Statistician, 49(2), 217–218. https://doi.org/10.2307/2684642
