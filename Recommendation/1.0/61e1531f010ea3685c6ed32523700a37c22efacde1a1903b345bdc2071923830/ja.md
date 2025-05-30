```
GiniIndex
```

[Gini Index](https://en.wikipedia.org/wiki/Gini_coefficient)は、通常、所得分配の不平等の度合いを測定するために使用されますが、`topk`推薦の文脈で多様性を評価するためにも適用できます：

$$
\frac{1}{|I| - 1} \sum_{j = 1}^{|I|} \left( (2j - |I| - 1) \cdot \frac{\left|\{u \mid u \in U \wedge i_j \in L_N(u) \}\right|}{N |U|} \right)
$$

```julia
measure(
    metric::GiniIndex, recommendations::AbstractVector{<:AbstractVector{<:Integer}};
    topk::Integer
)
```

インデックスは、推奨されたユーザーの数に関してすべてのアイテムが等しく選ばれた場合に0になります。
