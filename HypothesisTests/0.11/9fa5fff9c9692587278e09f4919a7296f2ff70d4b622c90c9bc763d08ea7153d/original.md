```
ADFTest(y::AbstractVector{T}, deterministic::Symbol, lag::Int) where T<:Real
```

Compute the augmented Dickey-Fuller unit root test.

`y` is the time series to be tested, `deterministic` determines the deterministic terms (options: `:none`, `:constant`, `:trend`, `:squared_trend`) and `lag` the number of lagged first-differences included in the test regression, respectively.

Critical values and asymptotic p-values are computed based on response surface regressions following MacKinnon (2010) and MacKinnon (1994), respectively. These may differ slightly from those reported in other regression packages as different algorithms might be used.

# References

  * James G. MacKinnon, 2010, "Critical values for cointegration tests," QED Working Paper No. 1227, 2010, [link](http://ideas.repec.org/p/qed/wpaper/1227.html).
  * James G. MacKinnon, 1994, "Approximate Asymptotic Distribution Functions for Unit-Root and Cointegration Tests", Journal of Business & Economic Statistics, Vol. 12, No. 2, pp. 167-176, [link](http://www.jstor.org/stable/1391481).

# External links

  * [Augmented Dickey-Fuller test on Wikipedia](https://en.wikipedia.org/wiki/Augmented_Dickey–Fuller_test)
