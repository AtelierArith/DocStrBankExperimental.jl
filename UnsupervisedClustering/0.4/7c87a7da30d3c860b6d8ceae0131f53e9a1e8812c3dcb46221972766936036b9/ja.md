```
fit(
    meta::GeneticAlgorithm,
    data::AbstractMatrix{<:Real},
    k::Integer
)
```

`fit` 関数は遺伝的アルゴリズムをクラスタリング問題に適用し、クラスタリングの結果を表す結果オブジェクトを返します。

# パラメータ:

  * `meta`: クラスタリングの設定とパラメータを表すインスタンス。
  * `data`: 各行がデータポイントを表し、各列が特徴を表す浮動小数点行列。
  * `k`: クラスタの数を表す整数。

# 例

```julia
n = 100
d = 2
k = 2

data = rand(n, d)

kmeans = Kmeans()
genetic_algorithm = GeneticAlgorithm(local_search = kmeans)
result = fit(genetic_algorithm, data, k)
```
