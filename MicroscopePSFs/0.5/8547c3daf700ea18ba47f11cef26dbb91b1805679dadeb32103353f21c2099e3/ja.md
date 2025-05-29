```
VectorPSF(nₐ::Real, λ::Real, dipole::DipoleVector;
            base_pupil::Union{Nothing, PupilFunction}=nothing,
            base_zernike::Union{Nothing, ZernikeCoefficients}=nothing,
            n_medium::Real=1.33,
            n_coverslip::Real=1.52,
            n_immersion::Real=1.52,
            z_stage::Real=0.0,
            grid_size::Integer=128)
```

ベクトルPSFを、瞳孔ベースまたはゼルニケベースのアプローチを使用して作成します。

# 引数

  * `nₐ`: 数値開口
  * `λ`: 波長（マイクロメートル単位）
  * `dipole`: ダイポールの方向ベクトル

# キーワード引数

  * `base_pupil`: オプションの基準収差瞳孔関数
  * `base_zernike`: オプションの基準収差のためのゼルニケ係数
  * `n_medium`: サンプル媒体の屈折率（デフォルト: 1.33）
  * `n_coverslip`: カバーガラスの屈折率（デフォルト: 1.52）
  * `n_immersion`: 没入媒体の屈折率（デフォルト: 1.52）
  * `z_stage`: サンプルステージがカバーガラスの名目焦点面から移動した距離（μm）（デフォルト: 0.0）
  * `grid_size`: 瞳孔グリッドのサイズ（デフォルト: 128）

# 戻り値

  * VectorPSF インスタンス
