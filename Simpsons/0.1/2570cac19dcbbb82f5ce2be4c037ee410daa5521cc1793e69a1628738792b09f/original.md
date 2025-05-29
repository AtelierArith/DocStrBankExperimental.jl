```
simpsons_analysis(df, cause_column, effect_column; verbose = true, show_plots = true)
```

Analyze the dataframe `df` assuming a cause is in `cause_column` and an effect in `effect_column` of the dataframe. Output data including any Simpson's paradox type reversals in subgroups found. Plots shown if show_plots is true (default).
