```
MedianVarianceBinning([minsize::Int = 10, maxbins::Int = typemax(Int)])
```

Dynamic binning scheme of the probability simplex with at most `maxbins` bins that each contain at least `minsize` samples.

The data set is split recursively as long as it is possible to split the bins while satisfying these conditions. In each step, the bin with the maximum variance of predicted probabilities for any component is selected and split at the median of the predicted probability of the component with the largest variance.
