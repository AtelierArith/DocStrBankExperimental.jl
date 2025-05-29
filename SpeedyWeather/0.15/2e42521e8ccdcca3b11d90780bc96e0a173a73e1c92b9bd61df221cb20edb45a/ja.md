ランダム渦度を初期条件として開始

  * `power::Float64`: [OPTION] スペクトル分布 k^power の指数
  * `amplitude::Float64`: [OPTION] （おおよその）振幅 [1/s]、球面調和係数の標準偏差として使用
  * `max_wavenumber::Int64`: [OPTION] 最大波数
  * `seed::Int64`: [OPTION] ランダム数生成器のシード、0=JuliaのGLOBAL_RNGからランダムにシード
  * `random_number_generator::Random.Xoshiro`: このランダムプロセスのための独立したランダム数生成器
