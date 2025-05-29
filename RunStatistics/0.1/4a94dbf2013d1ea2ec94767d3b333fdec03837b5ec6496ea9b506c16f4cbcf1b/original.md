```
squares_cdf(T_obs::Real, N::Integer)
```

Compute P(T < T*obs | N), the value of the cumulative distribution of the Squares statistic `T` at the  value `T*obs`observed in`N` independent trials with gaussian probability.

`T_obs` is the value of the test statistic for the observed data set; i.e., the largest `χ^2` of  any run of consecutive observed values above the expectation in a sequence of `N` independent trials  with Gaussian uncertainty. 

`N` is the total number of data points.

The calculation implements equations (16) and (17) from 

Frederik Beaujean and Allen Caldwell. *A Test Statistic for Weighted Runs.* Journal of Statistical Planning and Inference 141, no. 11 (November 2011): 3437–46. doi:10.1016/j.jspi.2011.04.022

https://arxiv.org/abs/1005.3233.
