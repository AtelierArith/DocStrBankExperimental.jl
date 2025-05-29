```
fit!(
    kmeans::Kmeans,
    data::AbstractMatrix{<:Real},
    result::KmeansResult
)
```

`fit!` 関数は、与えられた結果を初期点として k-means クラスタリングアルゴリズムを実行し、提供されたオブジェクトをクラスタリング結果で更新します。

# パラメータ:

  * `kmeans`: クラスタリング設定とパラメータを表すインスタンス。
  * `data`: 各行がデータポイントを表し、各列が特徴を表す浮動小数点行列。
  * `result`: クラスタリング結果で更新される結果オブジェクト。

# 例

```julia
n = 100
d = 2
k = 2

data = rand(n, d)

kmeans = Kmeans()
result = KmeansResult(n, [1.0 2.0; 1.0 2.0])
fit!(kmeans, data, result)
```
