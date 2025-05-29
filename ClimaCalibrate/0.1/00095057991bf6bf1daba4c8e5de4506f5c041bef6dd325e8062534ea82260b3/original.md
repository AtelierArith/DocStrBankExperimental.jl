```
analyze_iteration(ekp, g_ensemble, prior, output_dir, iteration)
```

After each evaluation of the observation map and before updating the ensemble, `analyze_iteration` is evaluated.

This function is optional to implement.

For example, one may want to print information from the `eki` object or plot `g_ensemble`.
