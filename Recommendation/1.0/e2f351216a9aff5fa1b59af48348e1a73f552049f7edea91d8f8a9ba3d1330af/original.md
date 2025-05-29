```
Recall
```

Recall-at-$k$ (Recall@$k$) indicates coverage of truth samples as a result of top-$k$ (`topk`) recommendation. The value is computed by the following equation:

$$
\mathrm{Recall@}k = \frac{|\mathcal{I}^+_u \cap I_N(u)|}{|\mathcal{I}^+_u|}.
$$

Here, $|\mathcal{I}^+_u \cap I_N(u)|$ is the number of *true positives*.

```
measure(
    metric::Recall,
    truth::AbstractVector{T},
    pred::AbstractVector{T},
    topk::Integer
)
```
