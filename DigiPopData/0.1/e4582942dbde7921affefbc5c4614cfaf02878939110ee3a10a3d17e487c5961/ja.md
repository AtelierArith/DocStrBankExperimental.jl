```
QuantileMetric <: AbstractMetric
```

QuantileMetricは、分位数データのためのメトリック記述子です。データの分位数とそれに対応する値に基づいています。

## フィールド

  * `size::Int`: データセットのサイズ。
  * `levels::Vector{Float64}`: 分位数レベル（例：0.25、0.5、0.75）。
  * `values::Vector{Float64}`: 分位数レベルに対応する値。
  * `skip_nan::Bool`: `true`の場合、シミュレーションデータにNaN値が許可され、無視されます。`false`の場合、NaN値は許可されません。
  * `cov_inv::Matrix{Float64}`: グループの共分散行列の逆行列。
  * `group_active::Vector{Bool}`: どのグループがアクティブ（非ゼロ率）であるかを示すブールベクトル。
  * `rates::Vector{Float64}`: 各グループの確率。

## コンストラクタ

  * `QuantileMetric(size::Int, levels::Vector{Float64}, values::Vector{Float64}; skip_nan::Bool = false)`: QuantileMetricの新しいインスタンスを作成します。入力データを検証し、逆共分散行列を計算します。
