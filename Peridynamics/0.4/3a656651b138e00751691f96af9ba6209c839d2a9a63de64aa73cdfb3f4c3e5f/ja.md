```
CRMaterial(; kernel, model, zem, dmgmodel, maxdmg)
```

非通常状態ベースのペリダイナミクスの局所連続体一貫（対応）定式化において、[`Body`](@ref) の材料を割り当てるために使用される材料タイプです。

# キーワード

  * `kernel::Function`: 点間の相互作用を重み付けするために使用されるカーネル関数。    (デフォルト: `linear_kernel`)    使用できるカーネルは以下の通りです：

      * [`linear_kernel`](@ref)
      * [`cubic_b_spline_kernel`](@ref)
  * `model::AbstractConstitutiveModel`: 材料の挙動を定義する構成モデル。    (デフォルト: `LinearElastic()`)    使用できるモデルは以下の通りです：

      * [`LinearElastic`](@ref)
  * `zem::AbstractZEMStabilization`: ゼロエネルギーモードの安定化。デフォルトではSilling (2017) の安定化アルゴリズムが使用されます。    (デフォルト: [`ZEMSilling`](@ref))
  * `dmgmodel::AbstractDamageModel`: 損傷挙動を定義する損傷モデル。    (デフォルト: [`CriticalStretch`](@ref))
  * `maxdmg::Float64`: 点が取得できる損傷の最大値。この値を超えると、その点のすべての結合が破壊される可能性があります。なぜなら、変形勾配が`NaN`値を含む可能性があるからです。    (デフォルト: `0.85`)

!!! note "破壊シミュレーションの安定性"
    この定式化は、ゼロエネルギーモードの安定化なしでは破壊シミュレーションに適していないことが知られています。したがって、破壊シミュレーションを行う際は注意し、`maxdmg`や`zem`の異なるパラメータを試してください。


# 例

```julia-repl
julia> mat = CRMaterial()
CRMaterial{LinearElastic, ZEMSilling, typeof(linear_kernel), CriticalStretch}(maxdmg=0.85)
```

---

```julia
CRMaterial{CM,ZEM,K,DM}
```

非通常状態ベースのペリダイナミクスの局所連続体一貫（対応）定式化のための材料タイプです。

# 型パラメータ

  * `CM`: 構成モデルの型。詳細はコンストラクタのドキュメントを参照してください。
  * `ZEM`: ゼロエネルギーモード安定化の型。詳細はコンストラクタのドキュメントを参照してください。
  * `K`: カーネル関数の型。詳細はコンストラクタのドキュメントを参照してください。
  * `DM`: 損傷モデルの型。詳細はコンストラクタのドキュメントを参照してください。

# フィールド

  * `kernel::Function`: 点間の相互作用を重み付けするために使用されるカーネル関数。詳細はコンストラクタのドキュメントを参照してください。
  * `model::AbstractConstitutiveModel`: 材料の挙動を定義する構成モデル。詳細はコンストラクタのドキュメントを参照してください。
  * `zem::AbstractZEMStabilization`: ゼロエネルギーモード安定化。詳細はコンストラクタのドキュメントを参照してください。
  * `dmgmodel::AbstractDamageModel`: 損傷挙動を定義する損傷モデル。詳細はコンストラクタのドキュメントを参照してください。
  * `maxdmg::Float64`: 点が取得できる損傷の最大値。詳細はコンストラクタのドキュメントを参照してください。

# 許可される材料パラメータ

[`Body`](@ref) に対して `CRMaterial` を使用して [`material!`](@ref) を実行する場合、次のパラメータが許可されます：材料パラメータ：

  * `horizon::Float64`: 点間相互作用の半径
  * `rho::Float64`: 密度

弾性パラメータ：

  * `E::Float64`: ヤング率
  * `nu::Float64`: ポアソン比
  * `G::Float64`: 剪断弾性率
  * `K::Float64`: 体積弾性率
  * `lambda::Float64`: 1番目のラメパラメータ
  * `mu::Float64`: 2番目のラメパラメータ

破壊パラメータ：

  * `Gc::Float64`: 臨界エネルギー放出率
  * `epsilon_c::Float64`: 臨界ひずみ

!!! note "弾性パラメータ"
    材料を指定するには、正確に2つの弾性パラメータが必要です。6つの許可された弾性パラメータの中から2つを選択してください。


# 許可されるエクスポートフィールド

[`Body`](@ref) に対して `CRMaterial` を使用して [`Job`](@ref) の `fields` キーワードを指定する場合、次のフィールドが許可されます：

  * `position::Matrix{Float64}`: 各点の位置
  * `displacement::Matrix{Float64}`: 各点の変位
  * `velocity::Matrix{Float64}`: 各点の速度
  * `velocity_half::Matrix{Float64}`: ヴェルレタイムソルバー用の速度パラメータ
  * `acceleration::Matrix{Float64}`: 各点の加速度
  * `b_int::Matrix{Float64}`: 各点の内部力密度
  * `b_ext::Matrix{Float64}`: 各点の外部力密度
  * `damage::Vector{Float64}`: 各点の損傷
  * `n_active_bonds::Vector{Int}`: 各点の無傷の結合の数
  * `stress::Matrix{Float64}`: 各点の応力テンソル
  * `von_mises_stress::Vector{Float64}`: 各点のフォン・ミーゼス応力
