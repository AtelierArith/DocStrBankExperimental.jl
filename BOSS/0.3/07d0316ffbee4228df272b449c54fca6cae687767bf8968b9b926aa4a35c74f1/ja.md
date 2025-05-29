初期データを格納します。

少なくとも1つの初期データポイントを提供する必要があります（実装上の理由から）。例えば、LatinHypercubeSampling.jlを使用して小さな初期グリッドを取得するか、単一のランダムな初期データポイントを提供することができます。

# フィールド

  * `X::AbstractMatrix{<:Real}`: 目的関数の入力を列として含みます。
  * `Y::AbstractMatrix{<:Real}`: 目的関数の出力を列として含みます。

参照: [`ExperimentDataPost`](@ref)
