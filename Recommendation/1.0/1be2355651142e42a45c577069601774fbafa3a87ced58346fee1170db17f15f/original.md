```
NDCG
```

Like MPR, normalized discounted cumulative gain (NDCG) computes a score for $I(u)$ which places emphasis on higher-ranked true positives. In addition to being a more well-formulated measure, the difference between NDCG and MPR is that NDCG allows us to specify an expected ranking within $\mathcal{I}^+_u$; that is, the metric can incorporate $\mathrm{rel}_n$, a relevance score which suggests how likely the $n$-th sample is to be ranked at the top of a recommendation list, and it directly corresponds to an expected ranking of the truth samples.

```
measure(
    metric::NDCG,
    truth::AbstractVector{T},
    pred::AbstractVector{T},
    topk::Integer
)
```
