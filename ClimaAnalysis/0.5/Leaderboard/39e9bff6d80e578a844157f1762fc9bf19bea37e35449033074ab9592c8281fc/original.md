```
match_category_order(rmse_var1::RMSEVariable, rmse_var2::RMSEVariable)
```

Make the order of categories of `rmse_var_src` matches the order of the categories of `rmse_var_dest`.

This function is helpful when changing the order of the categories in the plot produced by `ClimaAnalysis.Visualize.plot_boxplot!`.
