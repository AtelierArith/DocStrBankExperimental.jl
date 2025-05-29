```
Factor{TF, S} <: RegressionModel
```

因子モデルの推定からの結果とキャッシュ。このオブジェクトは、追加のメモリ割り当てなしでモデルを推定するために必要なすべての配列を保持します。[`fit`](@ref)および[`fit!`](@ref)も参照してください。

# フィールド

  * `Y::Matrix{TF}`: 各列が時系列に対応するデータ行列。
  * `Ystd::Matrix{TF}`: 列ごとに平均0、標準偏差1に標準化されたデータ。
  * `Ysd::Vector{TF}`: `Y`の各列の標準偏差。
  * `Yca::Matrix{TF}`: `Y`と同じサイズのキャッシュ。
  * `fac::Matrix{TF}`: モデルの因子; 観測された因子は最初の列に配置されます。
  * `crossfac::Matrix{TF}`: `fac'fac`および因子分解を保持するためのキャッシュ。
  * `Λ::Matrix{TF}`: モデルの負荷行列; 各行は`fac`の因子に対応します。
  * `crossΛu::Union{Matrix{TF}, Nothing}`: 因子と負荷行列を反復的に解決する必要があるときに必要なキャッシュ。
  * `svdca::Union{SDDcache{TF}, SVDcache{TF}, Nothing}`: 観測されていない因子が関与する場合の特異値分解のためのキャッシュ。
  * `nfaco::Int`: 観測された因子の数。
  * `resid::Matrix{TF}`: 標準化データ`Ystd`と推定された`fac`からの残差、`Y`のために負荷行列`Λ`をスケーリングする前。
  * `tss::Vector{TF}`: `Ystd`の各列の総平方和。
  * `rss::Vector{TF}`: `Ystd`の各列の残差平方和。
  * `r2::Vector{TF}`: `Ystd`の各列のr二乗。
  * `esample::BitVector`: `Y`を構築する際に元のデータテーブルから推定に関与する行のインジケーター; `Y`が与えられた後は推定に無関係。
