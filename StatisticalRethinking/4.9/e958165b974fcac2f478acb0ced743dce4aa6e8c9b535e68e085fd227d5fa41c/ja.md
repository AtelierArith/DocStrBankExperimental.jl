# link

標準化された変数のリンク関数を計算します。

```julia
link(dfa, vars, xrange)

```

### 必要な引数

  * `df::DataFrame`                      : DataFrameに変換されたチェーンサンプル
  * `vars::Vector{Symbol}`               : DataFrame内の変数（2つの変数）
  * `xrange::range`                      : リンク値が計算される範囲

### オプションの引数

  * `xbar::Float64`                      : 観測された予測子の平均値
  * `ybar::Float64`                      : 観測された結果の平均値（xbar引数が必要）

### 戻り値

  * `result`                             : リンク値のベクター
