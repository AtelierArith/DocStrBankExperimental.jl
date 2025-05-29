```
preaveraged_covariance(
    ts::SortedDataFrame,
    assets::Vector{Symbol} = get_assets(ts);
    regularisation::Union{Missing,Symbol} = :covariance_default,
    drop_assets_if_not_enough_data::Bool = false,
    regularisation_params::Dict = Dict(),
    only_regulise_if_not_PSD::Bool = false,
    theta::Real = 0.15,
    g::NamedTuple = g,
)
```

プレアベレージング法を使用した共分散行列の推定。

### 入力

  * `ts` - ティックデータ。
  * `assets` - ボラティリティを推定したい資産。
  * `regularisation` - 使用すべき正則化手法を表すシンボル。欠損の場合、正則化は行われません。
  * `drop_assets_if_not_enough_data` - 入力されたすべての`assets`に対して推定するための十分なデータがない場合、持っている資産の相関/ボラティリティのみを計算すべきか？
  * `regularisation_params` - 正則化アルゴリズムで使用されるキーワード引数。
  * `only_regulise_if_not_PSD` - 行列がすでにPSDでない場合にのみ正則化を試みるべきか。
  * `theta` - シータ値。詳細は論文を参照。
  * `g` - プレアベレージング法の関数（名前は "f"）とψ（名前は "psi"）の値を含むタプル。ここでのpsiは、ゼロから一の間の関数の積分であるべきです。

### 戻り値

  * `CovarianceMatrix`。

### 参考文献

Christensen K, Podolskij M, Vetter M (2013). “On covariation estimation for multivariate continuous Itô semimartingales with noise in non-synchronous observation schemes.” Journal of Multivariate Analysis, 120, 59–84. doi:10.1016/j.jmva.2013.05.002.
