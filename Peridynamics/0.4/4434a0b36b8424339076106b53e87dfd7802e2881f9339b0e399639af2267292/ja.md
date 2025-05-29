```
MultibodySetup(body_pairs...)
```

複数のボディを持つペリダイナミクスシミュレーションのセットアップ。

# 引数

  * `body_pairs::Pair{Symbol,<:AbstractBody}`: `:body_name => body_object` のペア。ボディの名前はシンボルとして指定する必要があります。

# 例外

  * 2つ未満のボディが定義されている場合はエラーが発生します。

# 例

```julia-repl
julia> sphere = Body(BBMaterial(), pos_sphere, vol_sphere)
280-point Body{BBMaterial{NoCorrection}}:
  1 point set(s):
    280-point set `all_points`

julia> plate = Body(BBMaterial(), pos_plate, vol_plate)
25600-point Body{BBMaterial{NoCorrection}}:
  1 point set(s):
    25600-point set `all_points`

julia> ms = MultibodySetup(:sphere => sphere, :plate => plate)
25880-point MultibodySetup:
  280-point Body{BBMaterial{NoCorrection}} with name `sphere`
  25600-point Body{BBMaterial{NoCorrection}} with name `plate`
```

---

!!! 警告 "内部使用のみ"     フィールドは内部使用のみを目的としていることに注意してください。これらはPeridynamics.jlの公開APIの一部ではなく、したがって、破壊的変更と見なされることなく、いつでも変更（または削除）される可能性があります。

```julia
MultibodySetup{Bodies}
```

# 型パラメータ

  * `Bodies <: Tuple`: マルチボディセットアップ内の異なるボディのすべてのタイプ。

# フィールド

  * `bodies::Bodies`: すべてのボディを含むタプル。
  * `body_names::Vector{Symbol}`: すべてのボディ名。
  * `body_idxs::Dict{Symbol,Int}`: ボディ名でボディインデックスを取得するための辞書。
  * `srf_contacts::Vector{ShortRangeForceContact}`: すべての短距離力接触。
