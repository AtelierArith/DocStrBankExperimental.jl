```
sensitivity_chrt(ArrayName::DataFrame, TargetCol, Chrt_Type=1)
```

Generate a horizontal bar chart summarizing sensitivity metrics for variables in a DataFrame, with special utility for analyzing Monte Carlo trials and exploratory data analysis.

# Description

This function computes pairwise correlations between one or more target columns and every column in the input DataFrame using both Spearman (rank) and Pearson correlation measures. In addition, it calculates a measure of contribution to variance based on the squared Spearman correlations. The function then builds a horizontal bar chart where:

  * When `Chrt_Type == 1`, the x-axis shows Spearman (rank) correlations.
  * When `Chrt_Type == 2`, the x-axis displays Pearson correlations.
  * For any other value of `Chrt_Type`, the x-axis presents the percentage contribution to variance.

Each variable is color-coded (red for negative correlations, blue for positive), providing an immediate visual cue about the direction of impact. The resulting chart is particularly helpful for assessing which inputs have the most significant effect on simulation outcomes, enabling users to prioritize variables for further analysis or model refinement.

# Arguments

  * `ArrayName::DataFrame`: A DataFrame containing your simulation or experimental data, where each column represents a different variable.
  * `TargetCol`: One or more column identifiers (symbols or strings) in `ArrayName` for which the sensitivity is to be measured. The function computes correlations between these target columns and all other columns.
  * `Chrt_Type`: An optional integer flag (default is `1`) to choose the metric for the x-axis:

      * `1` — Spearman correlation (Rank Correlation)
      * `2` — Pearson correlation
      * Any other value — Percentage contribution to variance (with sign)
