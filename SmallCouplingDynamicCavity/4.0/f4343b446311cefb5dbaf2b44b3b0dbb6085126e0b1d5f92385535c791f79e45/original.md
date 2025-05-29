```
ROC_curve(marg::Vector{Float64}, x::Vector{TI}) where {TI<:Integer}
```

Compute the Receiver Operating Characteristic (ROC) curve and the Area Under the Curve (AUC) based on inferred marginal probabilities and true configurations.

This function computes the ROC curve by sorting the marginal probabilities (`marg`) in decreasing order and sorting the true configuration (`x`) correspondingly. It then iterates over the sorted values to calculate the True Positive Rate (TPR) and False Positive Rate (FPR) at different thresholds, and computes the AUC.

# Arguments

  * `marg`: A vector containing the marginal probabilities of each node being infected at a fixed time.
  * `x`: The true configuration of the nodes at the same fixed time.

# Returns

  * `fp_rates`: Array of false positive rates corresponding to each threshold.
  * `tp_rates`: Array of true positive rates corresponding to each threshold.
  * `auc`: The Area Under the Curve (AUC) of the ROC curve.
