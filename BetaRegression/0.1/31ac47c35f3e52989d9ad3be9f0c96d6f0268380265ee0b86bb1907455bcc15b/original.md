```
coefnames(model::TableRegressionModel{<:BetaRegressionModel})
```

For a `BetaRegressionModel` fit using a table and `@formula`, return the names of the coefficients as a vector of strings. The precision term is included as the last element in the array and has name `"(Precision)"`.
