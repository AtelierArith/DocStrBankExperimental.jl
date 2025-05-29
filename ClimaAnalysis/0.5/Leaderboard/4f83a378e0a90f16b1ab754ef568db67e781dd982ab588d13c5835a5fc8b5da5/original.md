```
reorder_categories(rmse_var::RMSEVariable, categories::Vector{String})
```

Reorder the categories in `rmse_var` to match `categories`.

If a category in `categories` is not present in as a category in `rmse_var`, then an error is thrown. This function is helpful when changing the order of the categories in the plot produced by `ClimaAnalysis.Visualize.plot_boxplot!`.
