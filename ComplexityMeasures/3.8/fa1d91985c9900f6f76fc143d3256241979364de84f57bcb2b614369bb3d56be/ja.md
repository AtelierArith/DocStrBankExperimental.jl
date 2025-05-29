```
NaiveKernel(ϵ::Real; method = KDTree, w = 0, metric = Euclidean()) <: OutcomeSpace
```

[`OutcomeSpace`](@ref) は、「ナイーブ」カーネル密度推定アプローチ (KDE) に基づいており、[PrichardTheiler1995](@citet) で議論されています。

確率 $P(\mathbf{x}, \epsilon)$ は、$\mathbf{x}$ の周りの半径 `ϵ` のハイパー球が占める空間に他のポイントがいくつ存在するかをカウントすることによって、すべてのポイント $\mathbf{x}$ に割り当てられます。これは次のように表されます：

$$
P_i( X, \epsilon) \approx \dfrac{1}{N} \sum_{s} B(||X_i - X_j|| < \epsilon),
$$

ここで、$B$ は引数が `true` の場合に 1 を返します。確率はその後正規化されます。

## キーワード引数

  * `method = KDTree`: Neighborhood.jl によってサポートされる検索構造。具体的には、木構造に基づく近傍検索を使用するために `KDTree` を使用するか、すべてのポイント間の直接距離のために `BruteForce` を使用します。データの次元がデータの長さよりもはるかに小さい場合、KDTrees は直接距離を大幅に上回ります。
  * `w = 0`: 指定されたポイント $x_i$ から $|i - s| ≤ w$ の範囲内にあるインデックス $s$ を除外する Theiler ウィンドウ。
  * `metric = Euclidean()`: 距離メトリック。

## アウトカム空間

`NaiveKernel` のアウトカム空間 `Ω` は、入力データのインデックス `eachindex(x)` です。したがって、明確に定義された [`outcome_space`](@ref) のためには入力 `x` が必要です。データポイント自体を返さない理由は、重複するデータポイントが異なる近傍を持つために同じ確率が割り当てられない可能性があるからです。
