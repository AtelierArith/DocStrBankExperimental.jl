```
continuous_chain_ratio(dim, k) -> Floa64
```

次元 `dim` に対する連続体限界の予測連鎖比 $\langle \mathbf{C_k} \rangle / n^k$ を計算します。ここで、$C_k$ は [`count_relations`](@ref) によって計算された長さ `k` の厳密に昇順の連鎖の数であり、$n$ は causet 内の原子の数です。

予測される連続体限界は次の通りです：

$$
\frac{\langle \mathbf{C_k} \rangle}{n^k} = \frac{1}{k} \left( \frac{Γ(d+1)}{2} \right)^{k-1} \frac{Γ(d/2) Γ(d)}{Γ(kd/2) Γ((k+1)d/2)}
$$

`k = 2` の場合、これは [`continuous_relation_ratio`](@ref) に等しいです。
