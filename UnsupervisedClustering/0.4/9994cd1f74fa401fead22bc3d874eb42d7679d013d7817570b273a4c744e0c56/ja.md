```
fit(
    kmeans::Kmeans,
    data::AbstractMatrix{<:Real},
    initial_clusters::AbstractVector{<:Integer}
)
```

`fit` 関数は、与えられたデータポイントを初期点として k-means クラスタリングアルゴリズムを実行し、クラスタリング結果を表す結果オブジェクトを返します。

# パラメータ:

  * `kmeans`: クラスタリング設定とパラメータを表すインスタンス。
  * `data`: 各行がデータポイントを表し、各列が特徴を表す浮動小数点行列。
  * `initial_clusters`: 各クラスタの初期データポイントを表す整数ベクトル。

# 例

```julia
n = 100
d = 2
k = 2

data = rand(n, d)

kmeans = Kmeans()
result = fit(kmeans, data, [4, 12])
```
