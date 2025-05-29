```
squares_pvalue(T_obs::Real, N::Integer)
```

Compute P(T >= `T_obs` | `N`), the p value for the Squares test statistic `T` being larger or equal to `T_obs`,  the value of the Squares statistic observed in `N` datapoints. 

The Squares statistic `T` denotes the largest `χ^2` of any run of consecutive successes (above expectation) in a  sequence of `N` independent trials with Gaussian uncertainty.

Via `squares_cdf()` this function implements equations (16) and (17) from

Frederik Beaujean and Allen Caldwell. *A Test Statistic for Weighted Runs.* Journal of Statistical Planning and Inference 141, no. 11 (November 2011): 3437–46. doi:10.1016/j.jspi.2011.04.022

https://arxiv.org/abs/1005.3233.
