```
新規性
```

観察されていない推奨アイテムの数、すなわち `observed` に含まれていないアイテム。

```julia
measure(
    metric::Novelty, recommendations::Union{AbstractSet, AbstractVector};
    observed::Union{AbstractSet, AbstractVector}
)
```
