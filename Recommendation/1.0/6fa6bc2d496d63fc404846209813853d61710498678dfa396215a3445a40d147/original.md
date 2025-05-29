```
ShannonEntropy
```

If we focus more on individual items and how many users are recommended a particular item, the diversity of `topk` recommender can be defined by [Shannon Entropy](https://en.wikipedia.org/wiki/Entropy_(information_theory)):

$$
-\sum_{j = 1}^{|I|} \left( \frac{\left|\{u \mid u \in U \wedge i_j \in L_N(u) \}\right|}{N |U|} \ln \left( \frac{\left|\{u \mid u \in U \wedge i_j \in L_N(u) \}\right|}{N |U|}  \right) \right)
$$

where $i_j$ denotes $j$-th item in the available item set $I$.

```julia
measure(
    metric::ShannonEntropy, recommendations::AbstractVector{<:AbstractVector{<:Integer}};
    topk::Integer
)
```
