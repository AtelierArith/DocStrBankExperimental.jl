`struct NormalSpline{T, RK} <: AbstractSpline where {T <: AbstractFloat, RK <: ReproducingKernel_0}`

ノーマルスプラインの完全な情報を含む構造体を定義します

# フィールド

  * `_kernel`: 再生核スプラインが構築された
  * `_compression`: 元のノード位置を単位ハイパーキューブに変換するための係数
  * `_nodes`: 変換された関数値ノード
  * `_values`: 補間ノードでの関数値
  * `_d_nodes`: 変換された関数の方向微分ノード
  * `_es`: 正規化された微分方向
  * `_d_values`: 関数の方向微分値
  * `_min_bound`: 元のノード位置領域の最小境界
  * `_gram`: 問題のグラム行列
  * `_chol`: グラム行列のコレスキー分解
  * `_mu`: スプライン係数
  * `_cond`: グラム行列の条件数の推定
