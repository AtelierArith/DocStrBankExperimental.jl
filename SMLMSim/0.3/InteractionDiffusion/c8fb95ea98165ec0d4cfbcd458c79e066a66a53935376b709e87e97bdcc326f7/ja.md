```
simulate(params::DiffusionSMLMParams; 
         starting_conditions::Union{Nothing, SMLD, Vector{<:AbstractDiffusingEmitter}}=nothing,
         photons::Float64=1000.0, 
         override_count::Union{Nothing, Int}=nothing,
         kwargs...)
```

スモルホチュスキー拡散シミュレーションを実行し、フレーム番号とタイムスタンプ情報を持つエミッターを含むBasicSMLDオブジェクトを返します。

# 引数

  * `params::DiffusionSMLMParams`: シミュレーションパラメータ
  * `starting_conditions::Union{Nothing, SMLD, Vector{<:AbstractDiffusingEmitter}}`: オプションの開始エミッター
  * `photons::Float64=1000.0`: エミッターあたりの光子の数
  * `override_count::Union{Nothing, Int}=nothing`: 分子の数のオプションの上書き

# キーワード引数

  * 追加のパラメータは無視されます（他のシミュレートメソッドとの統一インターフェースを可能にします）

# 戻り値

  * `BasicSMLD`: すべてのフレームにわたるすべてのエミッターを含む単一のSMLDオブジェクト

# 例

```julia
# カメラ設定でパラメータを設定
params = DiffusionSMLMParams(
    density = 0.5,           # μm²あたりの分子数
    box_size = 10.0,         # μm
    camera_framerate = 20.0, # 20 fps
    camera_exposure = 0.04   # 40msの露光
)

# 基本的なシミュレーションを実行
smld = simulate(params)

# 正確に2つの粒子でシミュレーションを実行
smld = simulate(params; override_count=2)

# 前のシミュレーション状態を新しいシミュレーションの開始条件として使用
final_frame = maximum([e.frame for e in smld.emitters])
final_state_emitters = filter(e -> e.frame == final_frame, smld.emitters)
smld_continued = simulate(params; starting_conditions=final_state_emitters)
```
