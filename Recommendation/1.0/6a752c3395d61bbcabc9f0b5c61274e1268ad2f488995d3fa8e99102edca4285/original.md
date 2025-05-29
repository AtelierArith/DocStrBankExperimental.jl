```
ReciprocalRank
```

If we are only interested in the first true positive, reciprocal rank (RR) could be a reasonable choice to quantitatively assess the recommendation lists. For $n_{\mathrm{tp}} \in \left[ 1, |\mathcal{I}| \right]$, a position of the first true positive in $I(u)$, RR simply returns its inverse:

$$
  \mathrm{RR} = \frac{1}{n_{\mathrm{tp}}}.
$$

RR can be zero if and only if $\mathcal{I}^+_u$ is empty.

```
measure(
    metric::ReciprocalRank,
    truth::AbstractVector{T},
    pred::AbstractVector{T}
)
```
