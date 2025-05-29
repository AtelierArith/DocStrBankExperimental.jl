```
plot_shapley(df_shap, baseline_shap,
             range_shap::UnitRange = UnitRange(axes(df_shap,1));
             title::String         = "features $range_shap",
             dpi::Int              = 200)
```

Plot horizontal bar graph of feature importance (Shapley effects).

**Arguments:**

  * `df_shap`:       DataFrame of Shapley effects

| **Field**      | **Type** | **Description**     |
|:-------------- |:-------- |:------------------- |
| `feature_name` | `Symbol` | feature name        |
| `mean_effect`  | `Real`   | mean Shapley effect |

  * `baseline_shap`: intercept of Shapley effects
  * `range_shap`:    (optional) range of Shapley effects to plot (limit to length ~20)
  * `dpi`:           (optional) dots per inch (image resolution)
  * `title`:         (optional) plot title

**Returns:**

  * `p1`: plot of Shapley effects
