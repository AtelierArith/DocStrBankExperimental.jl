```
squares_pvalue_approx(T_obs::Real, L::Integer, [epsp::Real])
```

Compute an approximation of P(T >= `T_obs` | `L`), the p value for the Squares test  statistic T being larger or equal to `T_obs`,  the value of the Squares statistic observed in the data.  The total number of datapoints is `L = n * N`, if not defined otherwise, the function chooses the default values `N = 80` and `n = L / N`.

To specify a certain choice for `N` and `n`, do:

```
squares_pvalue_approx(T_obs::Real, Ns::AbstractArray,  [epsp::Real])
```

With `Ns` being an array holding `N::Integer` and `n::Real` as its first and second element: Ns = [N, n]

The accuracy's lower bound is `n * 10^(-14)`, a desired accuracy up to this boundary can be specified with the optional `epsp` argument. See documentation on Accuracy under `Guide/Details of computation`.

Via `squares_cdf_approx()` this function implements equation (17) from:

Frederik Beaujean and Allen Caldwell. *Is the bump significant? An axion-search example*

https://arxiv.org/abs/1710.06642
