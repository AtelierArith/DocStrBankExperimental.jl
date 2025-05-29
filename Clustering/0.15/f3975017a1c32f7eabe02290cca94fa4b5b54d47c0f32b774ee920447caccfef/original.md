```
confusion([T = Int],
          a::Union{ClusteringResult, AbstractVector},
          b::Union{ClusteringResult, AbstractVector}) -> Matrix{T}
```

Calculate the *confusion matrix* of the two clusterings.

Returns the 2×2 confusion matrix `C` of type `T` (`Int` by default) that represents partition co-occurrence or similarity matrix between two clusterings `a` and `b` by considering all pairs of samples and counting pairs that are assigned into the same or into different clusters.

Considering a pair of samples that is in the same group as a **positive pair**, and a pair is in the different group as a **negative pair**, then the count of true positives is `C₁₁`, false negatives is `C₁₂`, false positives `C₂₁`, and true negatives is `C₂₂`:

|          | Positive | Negative |
|:--------:|:--------:|:--------:|
| Positive |   C₁₁    |   C₁₂    |
| Negative |   C₂₁    |   C₂₂    |

## See also

[`counts(a::ClusteringResult, a::ClusteringResult)`](@ref counts) for full *contingency matrix*.
