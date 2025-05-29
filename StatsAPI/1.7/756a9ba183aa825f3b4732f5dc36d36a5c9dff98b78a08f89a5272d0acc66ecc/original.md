```
nullloglikelihood(model::StatisticalModel)
```

Return the log-likelihood of the null model, obtained by dropping all independent variables present in `model`.

If `model` includes an intercept, the null model is the one with only the intercept; otherwise, it is the one without any predictor (not even the intercept).
