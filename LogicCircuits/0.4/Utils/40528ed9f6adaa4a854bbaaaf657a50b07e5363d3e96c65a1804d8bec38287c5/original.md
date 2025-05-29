Return a copy of Imputed values of X  (potentially statistics from another DataFrame)

For example, to impute using same DataFrame:

```
impute(X; method=:median)
```

If you want to use another DataFrame to provide imputation statistics:

```
impute(test_x, train_x; method=:mean)
```

Supported methods are `:median`, `:mean`, `:one`, `:zero`
