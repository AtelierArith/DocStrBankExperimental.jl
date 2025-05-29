```
leave_future_out(model::UDE, training!, k; kwargs... )
```

Runs a leave future out cross validation on the UDe model `model` using the training routine `train!` with `k`  folds.  if a path to a csv file is provided usign the path key word then the raw testing data and forecasts will be saved for each fold.  

The funtion returns three data frames. The first contains an estimate of the mean aboslue error of the forecasts and assocaited standard error as a fuction of the forecast horizon (1 to k time steps into the future). The second and third are returned in a named tuple with two elements `horizon_by_var` and `raw`. The data frame `horizon_by_var` is containds the forecasting errors seperated by variable and the data frame `raw` contains the raw testing and forecasting data.  If the model is trained on multiple time series the named tupe will include a third data frame `horizon_by_var_by_series`.

```
# kwargs
```

  * `path`: the path to a directory to save the output dataframes, defaults to Null
