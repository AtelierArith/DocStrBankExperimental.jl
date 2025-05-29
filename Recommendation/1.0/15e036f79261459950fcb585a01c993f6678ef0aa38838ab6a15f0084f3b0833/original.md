```
MAP
```

While the original Precision@$N$ provides a score for a fixed-length recommendation list $I_N(u)$, mean average precision (MAP) computes an average of the scores over all recommendation sizes from 1 to $|\mathcal{I}|$. MAP is formulated with an indicator function for $i_n$, the $n$-th item of $I(u)$, as:

$$
\mathrm{MAP} = \frac{1}{|\mathcal{I}^+_u|} \sum_{n = 1}^{|\mathcal{I}|} \mathrm{Precision@}n \cdot  \mathbb{1}_{\mathcal{I}^+_u}(i_n).
$$

It should be noticed that, MAP is not a simple mean of sum of Precision@$1$, Precision@$2$, $\dots$, Precision@$|\mathcal{I}|$, and higher-ranked true positives lead better MAP.

```
measure(
    metric::MAP,
    truth::AbstractVector{T},
    pred::AbstractVector{T}
)
```
