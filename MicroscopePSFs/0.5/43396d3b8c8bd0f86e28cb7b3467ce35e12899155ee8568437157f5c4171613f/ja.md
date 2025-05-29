```
VectorPSF(nₐ::Real, λ::Real;
            base_pupil::Union{Nothing, PupilFunction}=nothing,
            base_zernike::Union{Nothing, ZernikeCoefficients}=nothing,
            n_medium::Real=1.33,
            n_coverslip::Real=1.52,
            n_immersion::Real=1.52,
            z_stage::Real=0.0,
            grid_size::Integer=128)
```

回転する双極子を持つベクトルPSFを作成します。これは、x、y、およびzの双極子方向の非コヒーレントな和としてモデル化されています。

# 引数

  * `nₐ`: 数値開口
  * `λ`: 波長（マイクロメートル単位）

# キーワード引数

  * `base_pupil`: オプションの基準収差瞳関数
  * `base_zernike`: 基準収差のためのオプションのゼルニケ係数
  * `n_medium`: サンプル媒体の屈折率（デフォルト: 1.33）
  * `n_coverslip`: カバーガラスの屈折率（デフォルト: 1.52）
  * `n_immersion`: 没入媒体の屈折率（デフォルト: 1.52）
  * `z_stage`: サンプルステージがカバーガラスの名目焦点面から移動した距離（μm）（デフォルト: 0.0）
  * `grid_size`: 瞳グリッドのサイズ（デフォルト: 128）

# 戻り値

  * 回転する双極子を表すVectorPSFインスタンス

# 注意事項

  * 強度は、三つの直交双極子方向の非コヒーレント平均として計算されます
  * amplitude()関数は回転する双極子には意味がなく、エラーをスローします
