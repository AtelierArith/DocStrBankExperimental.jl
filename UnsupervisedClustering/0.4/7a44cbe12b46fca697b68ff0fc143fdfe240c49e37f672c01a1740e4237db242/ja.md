```
fit!(
    kmedoids::Kmedoids,
    distances::AbstractMatrix{<:Real},
    result::KmedoidsResult
)
```

`fit!` 関数は、与えられた結果を初期点として k-medoids クラスタリングアルゴリズムを実行し、提供されたオブジェクトをクラスタリング結果で更新します。

# パラメータ:

  * `kmedoids`: クラスタリング設定とパラメータを表すインスタンス。
  * `distances`: データポイント間のペアワイズ距離を表す浮動小数点行列。
  * `result`: クラスタリング結果で更新される結果オブジェクト。

# 例

```julia
n = 100
d = 2
k = 2

data = rand(n, d)
distances = pairwise(SqEuclidean(), data, dims = 1)

kmedoids = Kmedoids()
result = KmedoidsResult(n, [1.0 2.0; 1.0 2.0])
fit!(kmedoids, distances, result)
```
