```
continuous_relation_ratio(dim) -> Float64
```

次元 `dim` に対する関係比 $\langle \mathbf{R} \rangle / n^2$ の予測連続体限界を計算します。ここで、$R$ は [`count_relations`](@ref) によって計算された関係の数であり、$n$ は causet 内の原子の数です。

予測連続体限界は次のようになります：

$$
\frac{\langle \mathbf{R} \rangle}{n^2} = \frac{Γ(d) Γ(d/2)}{4Γ(3d/2)}
$$

ここで、`d` は次元です。
