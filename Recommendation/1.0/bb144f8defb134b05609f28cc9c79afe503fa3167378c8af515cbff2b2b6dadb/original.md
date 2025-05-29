```
MPR
```

Mean percentile rank (MPR) is a ranking metric based on $r_{i} \in [0, 100]$, the percentile-ranking of an item $i$ within the sorted list of all items for a user $u$. It can be formulated as:

$$
\mathrm{MPR} = \frac{1}{|\mathcal{I}^+_u|} \sum_{i \in \mathcal{I}^+_u} r_{i}.
$$

$r_{i} = 0\%$ is the best value that means the truth item $i$ is ranked at the highest position in a recommendation list. On the other hand, $r_{i} = 100\%$ is the worst case that the item $i$ is at the lowest rank.

MPR internally considers not only top-$N$ recommended items also all of the non-recommended items, and it accumulates the percentile ranks for all true positives unlike MRR. So, the measure is suitable to estimate users' overall satisfaction for a recommender. Intuitively, $\mathrm{MPR} > 50\%$ should be worse than random ranking from a users' point of view.

```
measure(
    metric::MPR,
    truth::AbstractVector{T},
    pred::AbstractVector{T}
)
```
