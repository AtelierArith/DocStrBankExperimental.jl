```
カバレッジ
```

カタログカバレッジは、利用可能なすべてのアイテムのセットを表す `catalog` の中の推奨アイテムの比率です。

```julia
measure(
    metric::Coverage, recommendations::Union{AbstractSet, AbstractVector};
    catalog::Union{AbstractSet, AbstractVector}
)
```
