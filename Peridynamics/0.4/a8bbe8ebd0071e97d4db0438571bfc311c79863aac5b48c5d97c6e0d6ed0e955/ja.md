```
CKIMaterial(; dmgmodel)
```

連続運動学にインスパイアされたペリダイナミクス定式化を用いて、[`Body`](@ref)の材料を割り当てるために使用される材料タイプです。

# キーワード

  * `dmgmodel::AbstractDamageModel`: 損傷挙動を定義する損傷モデル。    (デフォルト: `CriticalStretch()`)

# 例

```julia-repl
julia> mat = CKIMaterial()
CKIMaterial(dmgmodel=CriticalStretch())
```

---

```julia
CKIMaterial{DM}
```

連続運動学にインスパイアされたペリダイナミクスフレームワークのための材料タイプです。

# 型パラメータ

  * `DM`: 損傷モデルの型。詳細についてはコンストラクタのドキュメントを参照してください。

# フィールド

  * `dmgmodel::AbstractDamageModel`: 損傷挙動を定義する損傷モデル。詳細についてはコンストラクタのドキュメントを参照してください。

# 許可される材料パラメータ

`CKIMaterial`を持つ[`Body`](@ref)に対して[`material!`](@ref)を使用する場合、次のパラメータが許可されます: 材料パラメータ:

  * `horizon::Float64`: 点間相互作用の半径。
  * `rho::Float64`: 密度。

弾性パラメータ:

  * `E::Float64`: ヤング率。
  * `nu::Float64`: ポアソン比。
  * `G::Float64`: 剪断弾性率。
  * `K::Float64`: 体積弾性率。
  * `lambda::Float64`: 1番目のラメパラメータ。
  * `mu::Float64`: 2番目のラメパラメータ。

破壊パラメータ:

  * `Gc::Float64`: 臨界エネルギー放出率。
  * `epsilon_c::Float64`: 臨界ひずみ。

相互作用パラメータ:

  * `C1::Float64`: 一隣接相互作用パラメータ。 (デフォルト: `0.0`)
  * `C2::Float64`: 二隣接相互作用パラメータ。 (デフォルト: `0.0`)
  * `C3::Float64`: 二隣接相互作用パラメータ。 (デフォルト: `0.0`)

!!! warning "相互作用パラメータの指定"
    いずれかの相互作用パラメータが[`material!`](@ref)で使用される場合、ヤング率とポアソン比は無視され、指定された相互作用パラメータのみがその相互作用から計算される力密度に影響を与えます。

    相互作用パラメータが指定されていない場合、ヤング率とポアソン比がこれらのパラメータをEkiz、Steinmann、およびJavili (2022)に従って計算するために使用されます。


!!! note "弾性パラメータ"
    材料を指定するには、正確に2つの弾性パラメータが必要です。6つの許可された弾性パラメータの中から2つを選択してください。


# 許可されるエクスポートフィールド

`CKIMaterial`を持つ[`Body`](@ref)の[`Job`](@ref)の`fields`キーワードを指定する場合、次のフィールドが許可されます:

  * `position::Matrix{Float64}`: 各点の位置。
  * `displacement::Matrix{Float64}`: 各点の変位。
  * `velocity::Matrix{Float64}`: 各点の速度。
  * `velocity_half::Matrix{Float64}`: ヴェルレタイムソルバーのための速度パラメータ。
  * `acceleration::Matrix{Float64}`: 各点の加速度。
  * `b_int::Matrix{Float64}`: 各点の内部力密度。
  * `b_ext::Matrix{Float64}`: 各点の外部力密度。
  * `damage::Vector{Float64}`: 各点の損傷。
  * `n_active_one_nis::Vector{Int}`: 各点の無傷の一隣接相互作用の数。
