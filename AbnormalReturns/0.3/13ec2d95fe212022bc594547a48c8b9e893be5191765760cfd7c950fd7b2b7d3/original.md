```
car(
    data::FixedTable{T, 2};
    minobs=0.8
) where {T}

car(
    data::FixedTable,
    rr::RegressionModel;
    minobs=0.8
)

car(
    data::IterateFixedTable{T, 2};
    minobs=0.8
) where {T, MNames, FNames}

car(
    data::IterateFixedTable,
    rrs::AbstractVector{<:BasicReg};
    minobs=0.8
)
```

Calculates the cumulative returns of a firm over a benchmark (through addition of each return). If a regression is passed, then the benchmark is based on the coefficients from that regression and the performance of the benchmarks in the regression. These are sometimes called Fama-French abnormal returns. If no regression is passed, abnormal returns are calculated as the difference between the first and second columns in the FixedTable (second column is typically the benchmark such as the S&P 500 or a value weighted return of all firms).

Similar to constructing the regression, passing an `IterateFixedTable` will return a Vector and uses a more optimized method.
