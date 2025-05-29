一次の自己回帰ランダム過程 (AR1) をスペクトル空間で、対応する `time_scales` と `standard_deviations` に対して独立に `wavenumbers` を進化させます。各時間ステップの後にグリッド空間に変換され、極値を制限するために `clamp` が適用されます。再現性のために `seed` を提供でき、各 `initialize!` で再シードされる独立した `random_number_generator` が使用されます。フィールドは次の通りです：

  * `trunc::Int64`
  * `time_scale::Dates.Second`: [OPTION] AR1過程の時間スケール
  * `wavenumber::Int64`: [OPTION] AR1過程の波数
  * `standard_deviation::Any`: [OPTION] AR1過程の標準偏差
  * `clamp::Tuple{NF, NF} where NF`: [OPTION] グリッド空間への変換後に値を制限する範囲
  * `seed::Int64`: [OPTION] ランダム数生成器のシード、0=JuliaのGLOBAL_RNGからランダムにシード
  * `random_number_generator::Random.Xoshiro`: このランダム過程のための独立したランダム数生成器
  * `autoregressive_factor::Base.RefValue`: 時間スケールとモデルの時間ステップの関数である事前計算された自己回帰因子 [1]
  * `noise_factors::Any`: 各総波数 l のための事前計算されたノイズ因子 [1]
