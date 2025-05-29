```
rand(S::MSeriesRing, term_range, v...)
```

Return a random element of the series ring $S$ with number of terms in the range given by `term_range` and where coefficients of the series are randomly generated in the base ring using the data given by `v`. The exponents of the variable in the terms will be less than the precision caps for the Ring $S$ when it was created.
