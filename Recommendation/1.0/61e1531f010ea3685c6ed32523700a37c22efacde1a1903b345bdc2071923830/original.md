```
GiniIndex
```

[Gini Index](https://en.wikipedia.org/wiki/Gini_coefficient), which is normally used to measure a degree of inequality in a distribution of income, can be applied to assess diversity in the context of `topk` recommendation:

$$
\frac{1}{|I| - 1} \sum_{j = 1}^{|I|} \left( (2j - |I| - 1) \cdot \frac{\left|\{u \mid u \in U \wedge i_j \in L_N(u) \}\right|}{N |U|} \right)
$$

```julia
measure(
    metric::GiniIndex, recommendations::AbstractVector{<:AbstractVector{<:Integer}};
    topk::Integer
)
```

The index is 0 when all items are equally chosen in terms of the number of recommended users.
