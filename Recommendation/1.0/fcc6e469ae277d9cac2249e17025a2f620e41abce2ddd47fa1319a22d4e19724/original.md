```
AggregatedDiversity
```

The number of distinct items recommended across all suers. Larger value indicates more diverse recommendation result overall.

```julia
measure(
    metric::AggregatedDiversity, recommendations::AbstractVector{<:AbstractVector{<:Integer}}
)
```

Let $U$ and $I$ be a set of users and items, respectively, and $L_N(u)$ a list of top-$N$ recommended items for a user $u$. Here, an aggregated diversity can be calculated as:

$$
\left| \bigcup\limits_{u \in U} L_N(u) \right|
$$
