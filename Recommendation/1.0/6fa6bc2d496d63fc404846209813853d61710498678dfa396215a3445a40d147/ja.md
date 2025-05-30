```
ShannonEntropy
```

特定のアイテムに対して推奨されるユーザーの数に焦点を当てると、`topk` レコメンダーの多様性は [Shannon Entropy](https://en.wikipedia.org/wiki/Entropy_(information_theory)) によって定義できます：

$$
-\sum_{j = 1}^{|I|} \left( \frac{\left|\{u \mid u \in U \wedge i_j \in L_N(u) \}\right|}{N |U|} \ln \left( \frac{\left|\{u \mid u \in U \wedge i_j \in L_N(u) \}\right|}{N |U|}  \right) \right)
$$

ここで、$i_j$ は利用可能なアイテムセット $I$ の $j$ 番目のアイテムを示します。

```julia
measure(
    metric::ShannonEntropy, recommendations::AbstractVector{<:AbstractVector{<:Integer}};
    topk::Integer
)
```
