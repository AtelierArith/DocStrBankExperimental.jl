数値積分器の単一積分ステップを実行します。

引数:

  * `rk4::RK4` 4次のルンゲ・クッタ数値積分器オブジェクト
  * `epc::Union{Real, Epoch}` 積分ステップの開始時刻
  * `dt::Real` 積分ステップサイズ
  * `x::AbstractArray{<:Real, 1}` 状態ベクトル
  * `phi::AbstractArray{<:Real, 2}` 積分ステップの開始時の状態遷移行列
