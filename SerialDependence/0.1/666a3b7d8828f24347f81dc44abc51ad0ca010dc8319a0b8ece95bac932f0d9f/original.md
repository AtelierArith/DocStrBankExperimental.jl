```
bootstrap_CI(Series, lags, coefficient, n_iter = 1000)
```

Provides 95% a confidence interval by shuffling 'Series' 'n_iter' times, computing the values of 'coefficient' then finding the value of the top and bottom 2,5% to get the interval. This is done for every point in 'lags' (can be costly if 'Series' is long).

Input :     - Series : input array of categorical data     - coef*func (**function**) : the function for which the CI needs to be computed.             'coefficient' can be one of the following **functions** : 'cramer*coefficient, cohen*coefficient, theils*U'.     - lags (Array{Int64,1}) : the lag values at which the analysis is conducted     - n_iter (Int64) : how many iterations are run for the bootstrap procedure. returns :     - top (Array{Float64,1}) : Array of values for the upper limit of the CI.     - bottom (Array{Float64,1}) : Array of values for the lower limit of the CI.
