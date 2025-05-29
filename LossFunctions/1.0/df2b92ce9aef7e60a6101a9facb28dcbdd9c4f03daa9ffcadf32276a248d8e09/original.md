```
WeightedMarginLoss{L,W} <: MarginLoss
```

Can an be used to represent a re-weighted version of some type of binary loss `L`. The weight-factor `W`, which must be in `[0, 1]`, denotes the relative weight of the positive class, while the relative weight of the negative class will be `1 - W`.
