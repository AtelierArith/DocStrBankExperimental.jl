```
simulate(params::StaticSMLMParams; 
         starting_conditions::Union{Nothing, SMLD, Vector{<:AbstractEmitter}}=nothing,
         pattern::Pattern=nothing,
         molecule::Molecule=GenericFluor(photons=1e4, k_off=50.0, k_on=1e-2),
         camera::AbstractCamera=IdealCamera(1:128, 1:128, 0.1))
```

現実的な点滅動力学と局所化不確実性を持つ静的SMLMデータを生成します。

# 引数

  * `params::StaticSMLMParams`: シミュレーションパラメータ
  * `starting_conditions::Union{Nothing, SMLD, Vector{<:AbstractEmitter}}`: パターンを生成する代わりに使用するオプションの開始条件
  * `pattern::Pattern`: 使用するパターン（デフォルトはparams.ndimsに依存）
  * `molecule::Molecule`: 点滅シミュレーション用の蛍光体モデル
  * `camera::AbstractCamera`: 検出シミュレーション用のカメラモデル

# 戻り値

  * `Tuple{BasicSMLD, BasicSMLD, BasicSMLD}`: (true*positions, model*kinetics, noisy_data)

      * true_positions: 真のエミッタ位置
      * model_kinetics: シミュレートされた点滅を持つ位置
      * noisy_data: 点滅と局所化不確実性を持つ位置

# 例

```julia
# パラメータを作成
params = StaticSMLMParams(
    density = 2.0,              # 2パターン/μm²
    σ_psf = 0.15,         # 150nm PSF幅
    minphotons = 100,     # 検出のための100光子
    ndatasets = 5,        # 5つの独立したデータセット
    nframes = 2000,       # 2000フレーム
    framerate = 100.0     # 1秒あたり100フレーム
)

# Nmerパターンでシミュレーションを実行
pattern = Nmer3D(n=6, d=0.2)
smld_true, smld_model, smld_noisy = simulate(params; pattern=pattern)

# カスタム開始条件で実行
custom_emitters = [
    Emitter2DFit{Float64}(x, y, 1.0, 0.0, 0.0, 0.0, 0.0, 0.0; track_id=i)
    for (i, (x, y)) in enumerate(zip(rand(10), rand(10)))
]
smld_true, smld_model, smld_noisy = simulate(params; starting_conditions=custom_emitters)
```

# 注意

  * `params.σ_psf`の値は、2Dおよび3Dの両方で横方向の不確実性（σx, σy）に直接使用されます。
  * 3Dシミュレーションの場合、軸方向の不確実性（σz）は3倍の係数でスケーリングされます（すなわち、σz = 3 * σ_psf）。
  * `starting_conditions`が提供されている場合、パターンを生成する代わりにそれが使用されます。
