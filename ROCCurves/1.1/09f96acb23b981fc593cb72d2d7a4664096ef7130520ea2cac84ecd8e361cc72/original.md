```
roc(pred_scores, real_scores)
```

Returns a tuple of vectors (FPR, TPR), where FPR = "False positive rate" and TPR = "True positive rate". Each score in `real_scores` is interpreted as positive if the score is positive. To plot the ROC curve using Plots.jl: `plot(FPR, TPR, linetype=:steppost)`.
