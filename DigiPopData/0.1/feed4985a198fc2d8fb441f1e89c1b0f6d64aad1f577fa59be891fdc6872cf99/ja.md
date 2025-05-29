```
CategoryMetric <: AbstractMetric
```

CategoryMetricはカテゴリカルデータのためのメトリック記述子です。これはグループ内の多項分布に基づいています。

## フィールド

  * `size::Int`: データセットのサイズ。
  * `groups::Vector{String}`: グループの名前。
  * `rates::Vector{Float64}`: 各グループの確率。
  * `cov_inv::Matrix{Float64}`: グループの共分散行列の逆行列。
  * `group_active::Vector{Bool}`: どのグループがアクティブ（非ゼロのレート）であるかを示すブールベクター。

## コンストラクタ

  * `CategoryMetric(size::Int, groups::Vector{String}, rates::Vector{Float64})`: CategoryMetricの新しいインスタンスを作成します。入力データを検証し、逆共分散行列を計算します。
