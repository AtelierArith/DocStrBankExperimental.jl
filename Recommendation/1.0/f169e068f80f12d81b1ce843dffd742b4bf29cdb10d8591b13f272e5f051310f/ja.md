```
セレンディピティ
```

推奨アイテムのすべてについて、関連性と予期しない度の積の合計を返します。

```julia
measure(
    metric::Serendipity, recommendations::Union{AbstractSet, AbstractVector};
    relevance::AbstractVector, unexpectedness::AbstractVector
)
```
