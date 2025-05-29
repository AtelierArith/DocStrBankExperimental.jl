データ行列 `X`,`Y` と最適化されたモデルパラメータおよびハイパーパラメータを格納します。

# フィールド

  * `X::AbstractMatrix{<:Real}`: 目的関数の入力を列として含みます。
  * `Y::AbstractMatrix{<:Real}`: 目的関数の出力を列として含みます。
  * `params::ModelParams`: MAPモデルの（ハイパ）パラメータを含みます。
  * `consistent::Bool`: パラメータが現在のデータセット（`X`, `Y`）を使用してフィッティングされている場合は真です。データセットを更新した後は `consistent = false` に設定され、パラメータを再フィッティングした後は `consistent = true` に設定されます。

参照: [`ExperimentDataBI`](@ref)
