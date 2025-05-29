```
validity_ratio(yhat::AbstractVector)
```

Ratio of valid predictions (score > 0) and all predictions. Allows to check if predictive performance is given for all predictions or a subset of the predictions.

# Arguments

  * `yhat::AbstractVector` : Prediction scores.

# Extended help

A limitation of SimSpread is that it is impossible to generate predictions for query nodes whose similarity to every source of the first network layer is below the similarity threshold α. In this case, the length of the feature vector is zero, resource spreading is not possible, and the predicted value is zero for all targets, therefore we need guardrails to correctly assess  performance as a function of the threshold α.

This characteristic of SimSpread can be seen as an intrinsic notion of its application domain. No target predictions are generated for query nodes outside SimSpread’s application domain instead of returning likely meaningless targets.

# References

1. Vigil-Vásquez & Schüller (2022). De Novo Prediction of Drug Targets and Candidates by Chemical Similarity-Guided Network-Based Inference. International Journal of Molecular Sciences, 23(17), 9666. https://doi.org/10.3390/ijms23179666
