Package: Forecast

```
loess(xv, yv;
      d = 0,
      q = 3*sum((!ismissing).(yv))÷4,
      rho = fill(1.0,length(yv)),
      exact = [], extra = [])

loess(yv;
      d = 0,
      q = 3*sum((!ismissing).(yv))÷4,
      rho = fill(1.0,length(yv)),
      exact = [], extra = [])
```

Return a funcion to smooth a vector of observations using locally weighted regressions.

Although loess can be used to smooth observations for any given number of independent variables, this implementation is univariate. The speed of loess can be greatly increased by using fast aproximations for the linear fitting calculations, however this implementation calculates allows as well for exact results.

The loess functionality and nomenclature follows the descriptions in:

"STL: A Seasonal, Trend Decomposition Procedure Based on Loess" Robert B. Cleveland, William S. Cleveland, Jean E. McRae, and Irma Terpenning. Journal of Official Statistics Vol. 6. No. 1, 1990, pp. 3-73 (c) Statistics Sweden.

# Arguments

  * `xv`: Observations' support, if not provided 1:length(yv) is used instead.
  * `yv`: Observation values.
  * `d`: Degree of the linear fit, it accepts values 0, 1 or 2, if 0 an estimation of `d` is calculated.
  * `q`: As q increases loess becomes smoother, when q tends to infinity loess tends to an ordinary least square poynomial fit of degree `d`. It defaults to the rounding of 3/4 of xv's non-missing values length.
  * `rho`: Weights expressing the reliability of the observations (e.g. if yi had variances σ^2*ki where ki where known, the rhoi could be 1/ki). It defaults to 1.
  * `exact`: Vector containing support values where exact loess will be calculated, the least values the faster will be loess. It defaults to an emtpy array. For series of 10 values or less exact loess is guaranteed.
  * `extra`: Vector containing support values where, besideds those values chosen by the heuristic, exact loess will be calculated.

# Returns

A function returning the exact loess for the values contained in `exact` and either exact loess or fast approximations for the rest.

# Examples

```julia-repl
n = 1000
x = sort(rand(n)*2*pi);
y = sin.(x) + randn(n);
f = Smoothers.loess(x,y)
isapprox(f(pi),0;atol=0.1) #true
[...]
```
