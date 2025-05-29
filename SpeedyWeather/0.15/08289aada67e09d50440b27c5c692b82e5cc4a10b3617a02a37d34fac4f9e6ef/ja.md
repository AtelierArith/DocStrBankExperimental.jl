リープフロッグ時間ステッピングは以下のフィールドによって定義されます

  * `trunc::Int64`: スペクトル解像度（球面調和の最大次数）
  * `nsteps::Int64`: 予測変数に同時に保存されるタイムステップの数
  * `Δt_at_T31::Dates.Second`: T31の時間ステップ（分単位）、`trunc`に線形スケール
  * `radius::AbstractFloat`: 球の半径 [m]、スケーリングに使用
  * `adjust_with_output::Bool`: 出力*dtに正確に整数タイムステップで到達するためにΔt*at*T31を調整
  * `robert_filter::AbstractFloat`: 計算モードを抑制するためのロバート（1966）時間フィルター係数
  * `williams_filter::AbstractFloat`: 3次精度のウィリアムズ時間フィルター（アメズクア 2011）係数
  * `Δt_millisec::Dates.Millisecond`: 指定された解像度での時間ステップΔt [ms]
  * `Δt_sec::AbstractFloat`: 指定された解像度での時間ステップΔt [s]
  * `Δt::AbstractFloat`: 指定された解像度での時間ステップΔt [s/m]、1/radiusでスケーリングされたもの
