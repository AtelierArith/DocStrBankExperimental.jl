```
fit(
    kmedoids::Kmedoids,
    distances::AbstractMatrix{<:Real},
    initial_clusters::AbstractVector{<:Integer}
)
```

`fit`関数は、与えられたデータポイントを初期点としてk-medoidsクラスタリングアルゴリズムを実行し、クラスタリング結果を表す結果オブジェクトを返します。

# パラメータ:

  * `kmedoids`: クラスタリング設定とパラメータを表すインスタンス。
  * `distances`: データポイント間のペアワイズ距離を表す浮動小数点行列。
  * `initial_clusters`: 各クラスタの初期データポイントである整数ベクトル。

# 例

```julia
n = 100
d = 2
k = 2

data = rand(n, d)
distances = pairwise(SqEuclidean(), data, dims = 1)

kmedoids = Kmedoids()
result = fit(kmedoids, distances, [4, 12])
```
