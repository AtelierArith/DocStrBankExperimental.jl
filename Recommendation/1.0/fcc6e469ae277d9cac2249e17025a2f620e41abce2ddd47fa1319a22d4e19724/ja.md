```
AggregatedDiversity
```

すべてのユーザーにわたって推奨される異なるアイテムの数。大きな値は、全体的により多様な推奨結果を示します。

```julia
measure(
    metric::AggregatedDiversity, recommendations::AbstractVector{<:AbstractVector{<:Integer}}
)
```

$$
U
$$

をユーザーの集合、$I$ をアイテムの集合、$L_N(u)$ をユーザー $u$ に対するトップ-$N$ 推奨アイテムのリストとします。ここで、集約された多様性は次のように計算できます：

$$
\left| \bigcup\limits_{u \in U} L_N(u) \right|
$$
