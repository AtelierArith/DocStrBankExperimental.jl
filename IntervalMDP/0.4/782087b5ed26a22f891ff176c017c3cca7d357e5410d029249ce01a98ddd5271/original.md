```
sum_lower(p::IntervalProbabilities)
```

Return the sum of lower bound transition probabilities from a source state or source/action pair to all target states. This is useful in efficiently implementing O-maximization, where we start with a lower bound probability assignment and iteratively, according to the ordering, adding the gap until the sum of probabilities is 1.
