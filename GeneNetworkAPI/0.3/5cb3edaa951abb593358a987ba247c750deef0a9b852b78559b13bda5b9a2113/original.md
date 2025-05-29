```
run_correlation(trait::String, dataset::String, group::String; tp:;String="sample",
                method::String="pearson", n_result::Int64=500,
                gn_url::String=gn_url())
```

This function correlates a `trait` in a `dataset` against all traits in a target database (`group`).

This query currently takes the following parameters:

  * trait (required): trait ID for which the correlation is wanted
  * dataset (required): dataset in which the trait occurs (use the short abbreviation)
  * group (required): group in which which the comparisons will be performed
  * tp: sample (default) | tissue
  * method: pearson (default) | spearman
  * n_result: maximum number of results to return (default = 500)
