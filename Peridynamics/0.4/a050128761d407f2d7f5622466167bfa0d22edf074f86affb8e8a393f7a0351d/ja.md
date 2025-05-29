```
BACMaterial(; kernel, model, dmgmodel, maxdmg)
```

チェンとスペンサー（2019）の結合関連対応定式化を用いて、[`Body`](@ref) の材料を割り当てるために使用される材料タイプです。

# キーワード

  * `kernel::Function`: 点間の相互作用を重み付けするために使用されるカーネル関数。   (デフォルト: `linear_kernel`)
  * `model::AbstractConstitutiveModel`: 材料の挙動を定義する構成モデル。   (デフォルト: `LinearElastic()`)
  * `dmgmodel::AbstractDamageModel`: 破壊挙動を定義する損傷モデル。   (デフォルト: `CriticalStretch()`)
  * `maxdmg::Float64`: 点が取得できる損傷の最大値。この値を超えると、その点のすべての結合が破壊される可能性があります。なぜなら、変形勾配が `NaN` 値を含む可能性があるからです。   (デフォルト: `0.85`)

# 例

```julia-repl
julia> mat = BACMaterial()
BACMaterial{LinearElastic, typeof(linear_kernel), CriticalStretch}()
```

---

```julia
BACMaterial{CM,K,DM}
```

チェンとスペンサー（2019）の結合関連対応定式化のための材料タイプです。

# 型パラメータ

  * `CM`: 構成モデルの型。詳細についてはコンストラクタのドキュメントを参照してください。
  * `K`: カーネル関数の型。詳細についてはコンストラクタのドキュメントを参照してください。
  * `DM`: 損傷モデルの型。

# フィールド

  * `kernel::Function`: 点間の相互作用を重み付けするために使用されるカーネル関数。
  * `model::AbstractConstitutiveModel`: 材料の挙動を定義する構成モデル。
  * `dmgmodel::AbstractDamageModel`: 破壊挙動を定義する損傷モデル。
  * `maxdmg::Float64`: 点が取得できる損傷の最大値。詳細についてはコンストラクタのドキュメントを参照してください。

# 許可される材料パラメータ

`BACMaterial` を持つ [`Body`](@ref) に対して [`material!`](@ref) を使用する場合、次のパラメータが許可されます：

  * `horizon::Float64`: 点間相互作用の半径。
  * `rho::Float64`: 密度。
  * `E::Float64`: ヤング率。
  * `nu::Float64`: ポアソン比。
  * `Gc::Float64`: 臨界エネルギー放出率。
  * `epsilon_c::Float64`: 臨界ひずみ。

# 許可されるエクスポートフィールド

`BACMaterial` を持つ [`Body`](@ref) の [`Job`](@ref) の `fields` キーワードを指定する場合、次のフィールドが許可されます：

  * `position::Matrix{Float64}`: 各点の位置。
  * `displacement::Matrix{Float64}`: 各点の変位。
  * `velocity::Matrix{Float64}`: 各点の速度。
  * `velocity_half::Matrix{Float64}`: ヴェルレタイムソルバーのための速度パラメータ。
  * `acceleration::Matrix{Float64}`: 各点の加速度。
  * `b_int::Matrix{Float64}`: 各点の内部力密度。
  * `b_ext::Matrix{Float64}`: 各点の外部力密度。
  * `damage::Vector{Float64}`: 各点の損傷。
  * `n_active_bonds::Vector{Int}`: 各点の無傷の結合の数。
