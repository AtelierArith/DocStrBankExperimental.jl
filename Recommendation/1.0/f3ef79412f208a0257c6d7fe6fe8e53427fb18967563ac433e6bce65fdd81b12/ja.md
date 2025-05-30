```
UserKNN(
    data::DataAccessor,
    n_neighbors::Integer,
    normalize::Bool=false
)
```

[ユーザーベースのCFをピアソン相関を使用して](https://dl.acm.org/citation.cfm?id=312682)。`n_neighbors`は隣接者の数$k$を表し、`normalize`は隣接者の評価の加重和が正規化されるかどうかを指定します。

この手法は、次の式によってユーザー間のペアに重みを与えます：

$$
s_{u, v} = \frac{ \sum_{i \in \mathcal{I}^+_{u \cap v}}  (r_{u, i} - \overline{r}_u) (r_{v, i} - \overline{r}_v)}
{ \sqrt{\sum_{i \in \mathcal{I}^+_{u \cap v}} (r_{u,i} - \overline{r}_u)^2} \sqrt{\sum_{i \in \mathcal{I}^+_{u \cap v}} (r_{v, i} - \overline{r}_v)^2} },
$$

ここで、$\mathcal{I}^+_{u \cap v}$はユーザー$u$と$v$の両方によって観察されたアイテムの集合であり、$r_{u, i}$は$R$の$(u, i)$要素を示します。さらに、$\overline{r}_u$と$\overline{r}_v$はそれぞれ、$i \in \mathcal{I}^+_{u \cap v}$に対する$r_{u, i}$と$r_{v, i}$の平均値です。重みを使用して、ユーザーベースのCFはターゲットユーザー$u$の上位$k$の最高重み付けユーザー（すなわち、最近傍）を選択し、$i \in \mathcal{I}^-_u$の欠損$r_{u, i}$を次のように予測します：

$$
r_{u, i} = \overline{r}_u + \frac{\sum^k_{t=1} \left(r_{\sigma(t), i} - \overline{r}_{\sigma(t)}\right) \cdot s_{u,\sigma(t)} }{ \sum^k_{t=1} s_{u,\sigma(t)} },
$$

ここで、$\sigma(t)$は$t$-th最近傍ユーザーを示します。最終的に、予測値によってアイテム$\mathcal{I}^-_u$をソートすることで、ユーザー$u$に対して推薦を行うことができます。

ユーザーベースのCFは、徐々に増加する大量のユーザーとその動的な嗜好により、すべてのユーザーのペアに対して類似性を頻繁に再計算する必要があるため、非常に非効率的であることに注意が必要です。
