状態導関数を計算します。

引数:

  * `epc::Epoch`: 現在のエポック
  * `x::AbstractArray{<:Real, 1}`: 衛星の状態ベクトル
  * `mass::Real`: 衛星の質量 [kg]
  * `area_drag`: 抵抗に影響を受ける速度向きの面積 [m^2]
  * `coef_drag`: 抵抗係数 [無次元]
  * `area_srp`: 太陽放射圧に影響を受ける太陽向きの面積 [m^2]
  * `coef_srp`: 反射率 [無次元]
  * `n_grav::Integer`: 重力モデルの次数 (デフォルト: 20)
  * `m_grav::Integer`: 重力モデルの階数 (デフォルト: 20)
  * `drag::Bool`: 力モデルに大砲球の大気抵抗を含めるか (デフォルト: `true`)
  * `srp::Bool`: 力モデルに平面の太陽放射圧を含めるか (デフォルト: `true`)
  * `moon::Bool`: 力モデルに第三体の月の重力を含めるか (デフォルト: `true`)
  * `sun::Bool`: 力モデルに第三体の太陽を含めるか (デフォルト: `true`)
  * `relativity::Bool`: 力モデルに相対論的効果を含めるか (デフォルト: `true`)

返り値:

  * `dx::AbstractArray{<:Float64, 1}`: 衛星の状態導関数、速度および加速度 [m; m/s]
