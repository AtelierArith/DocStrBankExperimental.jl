```
fit(
    kmedoids::Kmedoids,
    distances::AbstractMatrix{<:Real},
    k::Integer
)
```

`fit` 関数は k-medoids クラスタリングアルゴリズムを実行し、クラスタリング結果を表す結果オブジェクトを返します。

# パラメータ:

  * `kmedoids`: クラスタリング設定とパラメータを表すインスタンス。
  * `distances`: データポイント間のペアワイズ距離を表す浮動小数点行列。
  * `k`: クラスタの数を表す整数。

# 例

```julia
n = 100
d = 2
k = 2

data = rand(n, d)
distances = pairwise(SqEuclidean(), data, dims = 1)

kmedoids = Kmedoids()
result = fit(kmedoids, distances, k)
```
