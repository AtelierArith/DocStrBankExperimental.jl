初期条件としてランダム速度を開始します

  * `max_speed::Float64`: [OPTION] 最大速度 [ms⁻¹]
  * `truncation::Int64`: [OPTION] 切り捨て後の最大波数
  * `seed::Int64`: [OPTION] ランダム数生成器のシード、0=JuliaのGLOBAL_RNGからランダムにシード
  * `random_number_generator::Random.Xoshiro`: このランダムプロセスのための独立したランダム数生成器
