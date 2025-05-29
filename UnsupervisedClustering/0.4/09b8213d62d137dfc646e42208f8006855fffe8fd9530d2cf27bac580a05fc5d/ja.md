```
fit(
    meta::RandomSwap,
    data::AbstractMatrix{<:Real},
    k::Integer
)
```

`fit` 関数はクラスタリング問題にランダムスワップを適用し、クラスタリング結果を表す結果オブジェクトを返します。

# パラメータ:

  * `meta`: クラスタリング設定とパラメータを表すインスタンス。
  * `data`: 各行がデータポイントを表し、各列が特徴を表す浮動小数点行列。
  * `k`: クラスタの数を表す整数。

# 例

```julia
n = 100
d = 2
k = 2

data = rand(n, d)

kmeans = Kmeans()
random_swap = RandomSwap(local_search = kmeans)
result = fit(random_swap, data, k)
```
