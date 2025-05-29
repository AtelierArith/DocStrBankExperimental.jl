```julia
MinimizationProblem(objective, lower_bounds, upper_bounds)

```

最小化問題を定義します。

  * `objective` は `ℝᴺ` ベクトルを実数にマッピングする関数です。長さ `N` のすべての `AbstractVector` を受け入れる必要があります。
  * `lower_bounds` と `upper_bounds` は境界を定義し、それらの長さは暗黙的に次元 `N` を定義します。

結果のフィールドは、上記の名前でアクセス可能であるべきです。
