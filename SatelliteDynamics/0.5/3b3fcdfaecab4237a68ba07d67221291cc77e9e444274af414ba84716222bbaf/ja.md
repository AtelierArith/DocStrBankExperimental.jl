地球慣性状態表現と動力学モデルを使用した衛星軌道状態ベクトル。

初期状態遷移行列が提供されている場合、それは遷移行列がない場合に状態の伝播に使用されます。状態遷移行列がない場合は、状態のみが伝播されます。

属性:

  * `rk4::RK4` 状態伝播に使用される内部数値積分器
  * `dt::Real` デフォルトの伝播時間ステップ。すべてのステップはこのサイズになりますが、

状態ベクトルがこのステップサイズよりも小さい時間に伝播するように要求された場合は、それを行います。

  * `epc::Epoch` 状態のエポック
  * `x::AbstractArray{Float64, 1}` 状態ベクトル。地球中心慣性直交座標系の状態。
  * `phi::Union{Nothing, Array{Float64, 2}}` 状態遷移行列、または伝播開始時点に対する現在の時間における状態の部分導関数の行列

次の力モデルパラメータはキーワード引数として設定できます。

パラメータ:

  * `mass::Real`: 衛星の質量 [kg]
  * `area_drag`: 抵抗の影響を受ける速度向きの面積。[m^2]
  * `coef_drag`: 抵抗係数 [無次元]
  * `area_srp`: 抵抗の影響を受ける速度向きの面積。[m^2]
  * `coef_srp`: 反射率係数 [無次元]
  * `n_grav::Integer`: 重力モデルの次数 (デフォルト: 20)
  * `m_grav::Integer`: 重力モデルの階数 (デフォルト: 20)
  * `drag::Bool`: 力モデルに大砲の大気抵抗を含める (デフォルト: `true`)
  * `srp::Bool`: 力モデルに平面の太陽放射圧を含める (デフォルト: `true`)
  * `moon::Bool`: 力モデルに第三者の月の重力を含める (デフォルト: `true`)
  * `sun::Bool`: 力モデルに第三者の太陽を含める (デフォルト: `true`)
  * `relativity::Bool`: 力モデルに相対論的効果を含める (デフォルト: `true`)
