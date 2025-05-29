Clock構造体は、モデル時間、統合する日数、およびこれにかかる時間ステップの数を追跡します。

  * `time::Dates.DateTime`: 現在のモデル時間
  * `start::Dates.DateTime`: シミュレーションの開始時間
  * `period::Dates.Second`: 統合する期間
  * `timestep_counter::Int64`: シミュレーション中のすべての時間ステップをカウント
  * `n_timesteps::Int64`: 統合する時間ステップの数、`initialize!(::Clock, ::AbstractTimeStepper)`で設定
  * `Δt::Dates.Millisecond`: 時間ステップ
