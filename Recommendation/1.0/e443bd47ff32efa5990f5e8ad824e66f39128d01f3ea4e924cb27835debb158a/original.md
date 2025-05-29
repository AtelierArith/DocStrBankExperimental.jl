```
Precision
```

Precision-at-$k$ (Precision@$k$) evaluates correctness of a top-$k$ (`topk`) recommendation list $I_N(u)$ according to the portion of true positives in the list as:

$$
\mathrm{Precision@}k = \frac{|\mathcal{I}^+_u \cap I_N(u)|}{|I_N(u)|}.
$$

```
measure(
    metric::Precision,
    truth::AbstractVector{T},
    pred::AbstractVector{T},
    topk::Integer
)
```
