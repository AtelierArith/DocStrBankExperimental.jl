```
StaticSMLMParams <: SMLMSimParams
```

静的SMLMシミュレーションのためのパラメータ。

# フィールド

  * `density::Float64`: 粒子の平方ミクロンあたりの密度
  * `σ_psf::Float64`: PSF幅（ミクロン単位）
  * `minphotons::Int`: 検出のための最小光子数
  * `ndatasets::Int`: シミュレーションするデータセットの数
  * `nframes::Int`: データセットごとのフレーム数
  * `framerate::Float64`: 秒あたりのフレーム数
  * `ndims::Int`: 次元数（2または3）
  * `zrange::Vector{Float64}`: 3Dシミュレーションのための軸方向範囲 [min*z, max*z]

# 例

```julia
# デフォルトパラメータ
params = StaticSMLMParams()

# カスタムパラメータ
params = StaticSMLMParams(
    density = 2.0,              # 2粒子/μm²
    σ_psf = 0.15,         # 150nm PSF幅
    minphotons = 100,     # 検出のための最小光子数
    ndatasets = 5,        # 5つの独立したデータセット
    nframes = 2000,       # データセットごとの2000フレーム
    framerate = 100.0,    # 秒あたり100フレーム
    ndims = 3,            # 3Dシミュレーション
    zrange = [-2.0, 2.0]  # 4μmの軸方向範囲
)
```
