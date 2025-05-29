```
IntraListSimilarity
```

推奨アイテムのすべてのペア間の類似性の合計。大きな値は多様性が少ないことを示します。

  * 参考文献: [Improving Recommendation Lists Through Topic Diversification](http://files.grouplens.org/papers/ziegler-www05.pdf)

```julia
measure(
    metric::IntraListSimilarity, recommendations::Union{AbstractSet, AbstractVector};
    sims::AbstractMatrix
)
```
