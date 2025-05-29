```
setpanel(data, idname, timename; step, reftype, rotation)
setpanel(id::AbstractArray, time::AbstractArray; step, reftype, rotation)
```

特定の操作（例えば [`lag`](@ref) や [`diff`](@ref)）に必要な [`PanelStructure`](@ref) を宣言します。ユニットIDと時間値は、関連する列を含むテーブルまたは配列として提供できます。`timestep` は、`time` 配列が [`ScaledArray`](@ref) であり、[`settime`](@ref) によって返される場合を除き、指定する必要があります。

# 引数

  * `data`: `Tables.jl` 互換のデータテーブル。
  * `idname::Union{Symbol,Integer}`: `data` 内のユニットIDを含む列の名前。
  * `timename::Union{Symbol,Integer}`: `data` 内の時間値を含む列の名前。
  * `id::AbstractArray`: ユニットIDを含む配列（代替メソッドにのみ必要）。
  * `time::AbstractArray`: 時間値を含む配列（代替メソッドにのみ必要）。

# キーワード

  * `step=nothing`: 各時間間隔の長さ；指定されていない場合は `step=one(eltype(time))` を試してください。
  * `reftype::Type{<:Signed}=Int32`: [`PanelStructure`](@ref) の参照値の要素型。
  * `rotation=nothing`: 回転サンプリングデザインにおける回転グループ；参照値として [`RotatingTimeValue`](@ref) を使用します。

!!! note
    [`PanelStructure`](@ref) を作成するために使用された基礎データが変更された場合、変更は既存の [`PanelStructure`](@ref) のインスタンスには反映されません。`setpanel` を使用して新しいインスタンスを作成する必要があります。

