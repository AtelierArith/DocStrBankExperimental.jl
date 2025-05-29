```
Serendipity
```

Return a sum of relevance-unexpectedness multiplications for all recommended items.

```julia
measure(
    metric::Serendipity, recommendations::Union{AbstractSet, AbstractVector};
    relevance::AbstractVector, unexpectedness::AbstractVector
)
```
