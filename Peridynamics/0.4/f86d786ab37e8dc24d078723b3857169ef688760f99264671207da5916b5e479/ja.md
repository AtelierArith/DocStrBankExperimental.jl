```
BBMaterial()
BBMaterial{Correction}()
```

標準的な結合ベースのパラダイナミクスの定式化を用いて、[`Body`](@ref) の材料を割り当てるために使用される材料タイプです。

# キーワード

  * `dmgmodel::AbstractDamageModel`: 破壊挙動を定義する損傷モデル。   (デフォルト: `CriticalStretch()`)

可能な修正方法は次のとおりです。

  * [`NoCorrection`](@ref): 修正は適用されません。 (デフォルト)
  * [`EnergySurfaceCorrection`](@ref): Le と Bobaru (2018) のエネルギーベースの表面修正方法が適用されます。

# 例

```julia-repl
julia> mat = BBMaterial()
BBMaterial{NoCorrection}()

julia> mat = BBMaterial{EnergySurfaceCorrection}()
BBMaterial{EnergySurfaceCorrection}()
```

---

```julia
BBMaterial{Correction}
```

結合ベースのパラダイナミクスの定式化のための材料タイプです。

# 型パラメータ

  * `Correction`: 修正アルゴリズムのタイプ。詳細についてはコンストラクタのドキュメントを参照してください。
  * `DM`: 損傷モデルのタイプ。

# 許可される材料パラメータ

`BBMaterial` を持つ [`Body`](@ref) に対して [`material!`](@ref) を使用する場合、次のパラメータが許可されます: 材料パラメータ:

  * `horizon::Float64`: 点間相互作用の半径。
  * `rho::Float64`: 密度。

弾性パラメータ

  * `E::Float64`: ヤング率。
  * `G::Float64`: せん断弾性率。
  * `K::Float64`: 体積弾性率。
  * `lambda::Float64`: 1番目のラメパラメータ。
  * `mu::Float64`: 2番目のラメパラメータ。

破壊パラメータ:

  * `Gc::Float64`: 臨界エネルギー放出率。
  * `epsilon_c::Float64`: 臨界ひずみ。

!!! note "ポアソン比と結合ベースのパラダイナミクス"
    結合ベースのパラダイナミクスでは、ポアソン比は3Dシミュレーションに対して1/4に制限されています。したがって、追加の弾性パラメータは1つだけ必要です。オプションとして、パラメータの組み合わせが `nu = 1/4` になる場合、2番目のキーワードの指定が許可されます。


# 許可されるエクスポートフィールド

`BBMaterial` を持つ [`Body`](@ref) の [`Job`](@ref) の `fields` キーワードを指定する場合、次のフィールドが許可されます:

  * `position::Matrix{Float64}`: 各点の位置。
  * `displacement::Matrix{Float64}`: 各点の変位。
  * `velocity::Matrix{Float64}`: 各点の速度。
  * `velocity_half::Matrix{Float64}`: ヴェルレタイムソルバーのための速度パラメータ。
  * `acceleration::Matrix{Float64}`: 各点の加速度。
  * `b_int::Matrix{Float64}`: 各点の内部力密度。
  * `b_ext::Matrix{Float64}`: 各点の外部力密度。
  * `damage::Vector{Float64}`: 各点の損傷。
  * `n_active_bonds::Vector{Int}`: 各点の無傷の結合の数。
