```
fill_surrogate_test!(test::SurrgateTest) → rval, vals
```

Perform the computations foreseen by `test` and return the value of the discriminatory statistic for the real data `rval` and the distribution of values for the surrogates `vals`.

This function is called by `pvalue`.
