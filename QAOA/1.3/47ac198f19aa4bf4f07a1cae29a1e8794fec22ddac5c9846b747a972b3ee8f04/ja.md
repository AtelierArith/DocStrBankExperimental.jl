```
partition_problem(a::Vector{Float64}; num_layers::Int=1, driver=X)
```

パーティション問題のインスタンスを設定するラッパー関数。

### 入力

  * `a::Vector{Float64}`: パーティションされる数の入力ベクトル。
  * `num_layers::Int=1` (オプション): 通常$p$で示されるQAOAレイヤーの数。
  * `driver=X` (オプション): QAOAで使用されるドライバーまたはミキサー。

### 出力

  * すべての関連量を保持する`Problem`構造体のインスタンス。

### 注意事項

一様に分布した数の集合$\mathcal{S} = \{a_1, ..., a_N\}$に対するパーティション問題は、2つの部分集合$\mathcal{S}_{1} \cup \mathcal{S}_2 =  \mathcal{S}$を見つけることから成り立ち、2つの部分集合$\mathcal{S}_{1, 2}$の合計の差ができるだけ小さくなるようにします。イジング形式のコスト関数は次のように定義できます。

$$
\hat C = -\left(\sum_{i=1}^{N} a_i \hat{Z}_i\right)^2 = \sum_{i<j\leq N} J_{ij} \hat{Z}_i \hat{Z}_j + \mathrm{const.}
$$

ここで、$J_{ij}=-2a_i a_j$です。目標は$\hat C$を*最大化*することです。
