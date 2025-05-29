```
LjungBoxTest(data::Vector{T}, vars::Vector{T}, lag::Integer=1)
```

Compute the Ljung-Box `Q` statistic to test the null hypothesis of independence in the violations/hits sequence that is implied by the vectors of realizations (`data`) and Value-at-Risk forecasts(`vars`). `lag` specifies the number of lags used in the construction of `Q`
