```
fit!(
    gmm::GMM,
    data::AbstractMatrix{<:Real},
    result::GMMResult
)
```

`fit!` 関数は、与えられた結果を初期点として GMM クラスタリングアルゴリズムを実行し、提供されたオブジェクトをクラスタリング結果で更新します。

# パラメータ:

  * `gmm`: クラスタリング設定とパラメータを表すインスタンス。
  * `data`: 各行がデータポイントを表し、各列が特徴を表す浮動小数点行列。
  * `result`: クラスタリング結果で更新される結果オブジェクト。

# 例

```julia
n = 100
d = 2
k = 2

data = rand(n, d)

gmm = GMM(estimator = EmpiricalCovarianceMatrix(n, d))
result = GMMResult(n, [[1.0, 1.0], [2.0, 2.0]])
fit!(gmm, data, result)
```
