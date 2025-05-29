```
init_mutunerlogger(;
    # キーワード引数
    target_density::T,
    inverse_temperature::T,
    system_size::Int,
    intensive_energy_scale::T = 1.0,
    initial_chemical_potential::T = 0.0,
    memory_fraction::T = 0.5,
    complex_sign_problem::Bool = false,
) where {T<:AbstractFloat}
```

与えられたパラメータで[`MuTunerLogger`](@ref)インスタンスを初期化します。

# キーワード引数

  * `target_density::T`: 目標粒子密度 $\langle n \rangle$。
  * `inverse_temperature::T`: 逆温度 $\beta$。
  * `system_size::Int`: システムサイズ $V$。
  * `intensive_energy_scale::T = 1.0`: 特徴的な集中的エネルギースケール $u_0$。
  * `initial_chemical_potential::T = 0.0`: 化学ポテンシャル $\mu$ の初期推定。
  * `memory_fraction::T = 0.5`: 忘却平均と分散を計算する際に保持され使用される測定履歴の割合。
  * `complex_sign_problem::Bool = false`: trueの場合、モンテカルロシミュレーションは複雑な符号問題に悩まされ、モンテカルロ重みが複素数になります。
