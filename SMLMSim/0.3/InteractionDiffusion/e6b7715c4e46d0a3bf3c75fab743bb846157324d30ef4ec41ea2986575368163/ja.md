```
DiffusionSMLMParams <: SMLMSimParams
```

スモルホフスキー動力学を用いた拡散ベースのSMLMシミュレーションのためのパラメータ。

# フィールド

  * `density::Float64`: 数密度 (分子/μm²)
  * `box_size::Float64`: シミュレーションボックスのサイズ (μm)
  * `diff_monomer::Float64`: モノマーの拡散係数 (μm²/s)
  * `diff_dimer::Float64`: ダイマーの拡散係数 (μm²/s)
  * `diff_dimer_rot::Float64`: ダイマーの回転拡散係数 (rad²/s)
  * `k_off::Float64`: ダイマー解離速度 (s⁻¹)
  * `r_react::Float64`: 反応半径 (μm)
  * `d_dimer::Float64`: ダイマー内のモノマーの間隔 (μm)
  * `dt::Float64`: タイムステップ (s)
  * `t_max::Float64`: 総シミュレーション時間 (s)
  * `ndims::Int`: 次元数 (2または3)
  * `boundary::String`: 境界条件のタイプ ("周期的"または"反射")
  * `camera_framerate::Float64`: カメラのフレームレート (Hz)
  * `camera_exposure::Float64`: フレームごとのカメラ露光時間 (s)

# 例

```julia
# デフォルトパラメータ
params = DiffusionSMLMParams()

# カスタムパラメータ
params = DiffusionSMLMParams(
    density = 1.0,           # 1分子/μm²
    box_size = 20.0,         # 20μm × 20μm ボックス
    diff_monomer = 0.2,      # 0.2 μm²/s
    diff_dimer = 0.1,        # 0.1 μm²/s
    diff_dimer_rot = 0.8,    # 0.8 rad²/s
    k_off = 0.1,             # 0.1 s⁻¹
    r_react = 0.02,          # 20nmの反応半径
    d_dimer = 0.06,          # 60nmのダイマー間隔
    dt = 0.005,              # 5msのタイムステップ
    t_max = 20.0,            # 20sのシミュレーション
    ndims = 3,               # 3Dシミュレーション
    boundary = "reflecting", # 反射境界
    camera_framerate = 20.0, # 1秒あたり20フレーム
    camera_exposure = 0.04   # フレームごとの露光時間40ms
)
```
