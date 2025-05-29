```
quantile_space(A, B; n = 50) → Aq, Bq, q
```

Express the array `B` into the quantile space of `A`. `B, A` must have the same indices.

The array `B` is binned according to the quantile values of the elements of `A`. `n` bins are created in total and the bin edges `p` are returned. The `i`-th bin contains data whose `A`-quantile values are ∈ [`q[i]`, `q[i+1]`). The indices of these `A` values are used to group `B`.

In each bin, the binned values of `A, B` are averaged, resulting in `Aq, Bq`.

The amount of datapoints per quantile is by definition `length(A)/n`.
