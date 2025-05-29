```
contact!(multibody_setup, name_body_a, name_body_b; kwargs...)
```

ボディ `name_body_a` と `name_body_b` の間に短距離力接触を定義します。これは [`MultibodySetup`](@ref) `multibody_setup` において行われます。

# 引数

  * `multibody_setup::MultibodySetup`: [`MultibodySetup`](@ref)。
  * `name_body_a::Symbol`: このマルチボディセットアップ内のボディの名前。
  * `name_body_b::Symbol`: このマルチボディセットアップ内のボディの名前。

# キーワード

  * `radius::Float64`: 接触検索半径。ボディ `name_body_a` の点とボディ `name_body_b` の点の距離がこの半径よりも小さい場合、接触力が計算されます。この半径は点クラウドの点間隔のオーダーであるべきです。
  * `penalty_factor::Float64`: 短距離力接触アルゴリズムのペナルティファクター。（デフォルト: `1e12`）

# 例外

  * `multibody_setup` に `name_body_a` と `name_body_b` という名前のボディが含まれていない場合、エラーが発生します。
  * キーワード `radius` が指定されていないか、`radius ≤ 0` の場合、エラーが発生します。
  * `penalty_factor ≤ 0` の場合、エラーが発生します。

# 例

```julia-repl
julia> ms = MultibodySetup(:a => body_a, :b => body_b)
2000-point MultibodySetup:
  1000-point Body{BBMaterial{NoCorrection}} with name `b`
  1000-point Body{BBMaterial{NoCorrection}} with name `b`

julia> contact!(ms, :a, :b; radius=0.001)

julia> ms
2000-point MultibodySetup:
  1000-point Body{BBMaterial{NoCorrection}} with name `b`
  1000-point Body{BBMaterial{NoCorrection}} with name `b`
  2 short range force contact(s)
```
