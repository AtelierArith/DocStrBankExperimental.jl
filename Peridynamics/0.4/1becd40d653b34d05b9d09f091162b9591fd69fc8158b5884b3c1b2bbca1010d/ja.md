```
OSBMaterial(; kernel, dmgmodel)
OSBMaterial{Correction}(; kernel, dmgmodel)
```

通常の状態ベースのペリダイナミクスの定式化を使用して、[`Body`](@ref) の材料を割り当てるために使用される材料タイプです。

可能な修正方法は次のとおりです：

  * [`NoCorrection`](@ref): 修正は適用されません。（デフォルト）
  * [`EnergySurfaceCorrection`](@ref): Le と Bobaru (2018) のエネルギーベースの表面修正方法が適用されます。

# キーワード

  * `kernel::Function`: 点間の相互作用を重み付けするために使用されるカーネル関数。   （デフォルト: `linear_kernel`）
  * `dmgmodel::AbstractDamageModel`: 損傷挙動を定義する損傷モデル。   （デフォルト: `CriticalStretch()`）

# 例

```julia-repl
julia> mat = OSBMaterial()
OSBMaterial{NoCorrection}(dmgmodel=CriticalStretch())

julia> mat = OSBMaterial{EnergySurfaceCorrection}()
OSBMaterial{EnergySurfaceCorrection}(dmgmodel=CriticalStretch())
```

---

```julia
OSBMaterial{Correction,K,DM}
```

通常の状態ベースのペリダイナミクスの定式化のための材料タイプです。

# 型パラメータ

  * `Correction`: 修正アルゴリズムの型。詳細についてはコンストラクタのドキュメントを参照してください。
  * `K`: カーネル関数の型。詳細についてはコンストラクタのドキュメントを参照してください。
  * `DM`: 損傷モデルの型。詳細についてはコンストラクタのドキュメントを参照してください。

# フィールド

  * `kernel::Function`: 点間の相互作用を重み付けするために使用されるカーネル関数。
  * `dmgmodel::AbstractDamageModel`: 損傷挙動を定義する損傷モデル。詳細についてはコンストラクタのドキュメントを参照してください。

# 許可される材料パラメータ

`OSBMaterial`を持つ[`Body`](@ref)に対して[`material!`](@ref)を使用する場合、次のパラメータが許可されます：材料パラメータ：

  * `horizon::Float64`: 点間相互作用の半径。
  * `rho::Float64`: 密度。

弾性パラメータ：

  * `E::Float64`: ヤング率。
  * `nu::Float64`: ポアソン比。
  * `G::Float64`: 剪断弾性率。
  * `K::Float64`: 体積弾性率。
  * `lambda::Float64`: 1番目のラメパラメータ。
  * `mu::Float64`: 2番目のラメパラメータ。

破壊パラメータ：

  * `Gc::Float64`: 臨界エネルギー放出率。
  * `epsilon_c::Float64`: 臨界ひずみ。

!!! note "弾性パラメータ"
    材料を指定するには、正確に2つの弾性パラメータが必要です。6つの許可された弾性パラメータの中から2つを選択してください。


# 許可されるエクスポートフィールド

`OSBMaterial`を持つ[`Body`](@ref)の[`Job`](@ref)の`fields`キーワードを指定する場合、次のフィールドが許可されます：

  * `position::Matrix{Float64}`: 各点の位置。
  * `displacement::Matrix{Float64}`: 各点の変位。
  * `velocity::Matrix{Float64}`: 各点の速度。
  * `velocity_half::Matrix{Float64}`: ヴェルレタイムソルバーのための速度パラメータ。
  * `acceleration::Matrix{Float64}`: 各点の加速度。
  * `b_int::Matrix{Float64}`: 各点の内部力密度。
  * `b_ext::Matrix{Float64}`: 各点の外部力密度。
  * `damage::Vector{Float64}`: 各点の損傷。
  * `n_active_bonds::Vector{Int}`: 各点の無傷の結合の数。
