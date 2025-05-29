```
cramer_coefficient(Serie, Lags::Array{Int64,1})
```

Returns the cramer's V coefficient for the given 'Lags' values.

Cramer's v is used in categorical data analysis to test the degree of association between a given set of categorical variable and another set of variables (example : eye color and hair color). Here, it measures the association between the categorical values of a time series, and the values at a later lagged time.

V lies in [0,1]. 0 no association, 1 perfect association. It is symmetric, meaning v(A,B) = v(B,A), so the information contained in the asymmetry between the variables is lost.

```
input :
- Serie : the time series containing the data
- Lags : Array containing the lags at which V will be computed. If an int is given
            a single point value will be returned.

output :
- V : the values of v for the given lags.
```
