```
ModelComparison(DM1::AbstractDataModel, DM2::AbstractDataModel) -> Tuple{Int,Real}
```

Compares the AICc values of both models at best fit and estimates probability that one model is more likely than the other. First entry of tuple returns which model is more likely to be correct (1 or 2) whereas the second entry returns the ratio of probabilities `p_better/p_worse`.
