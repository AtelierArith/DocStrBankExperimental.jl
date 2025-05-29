```
CovarianceMatrix(correlation::Hermitian{R},
    volatility::Vector{R},
    labels::Vector{Symbol}) where R<:Real
```

This `Struct` stores three elements. A `Hermitian` correlation matrix, a vector of volatilities and a vector of labels. The order of the labels matches the order of the assets in the volatility vector and correlation matrix. The default constructor is used.

### Inputs

  * `correlation` - A `Hermitian` correlation matrix.
  * `volatility` - Volatilities for each asset.
  * `labels` - The labels for the `correlation` and `volatility` members. The n'th entry of the `labels` vector should contain the name of the asset that has its volatility in the n'th entry of the `volatility` member and its correlations in the n'th row/column of the `correlation` member.
  * `time_period_per_unit` - The period that one unit of volatility corresponds to.

### Returns

  * A `CovarianceMatrix`.
