```
PanelStructure{R<:Signed, IP<:AbstractVector, TP<:AbstractVector}
```

ユニークなユニットIDと時間期間の組み合わせによって定義されるパネルデータ構造。これは、[`lag`](@ref)や[`diff`](@ref)などの特定の操作に必要な情報を含んでいます。さらに[`setpanel`](@ref)も参照してください。

# フィールド

  * `refs::Vector{R}`: 差分を取ることで時間のギャップを取得できる参照値。
  * `invrefs::Dict{R, Int}`: `refs`からインデックスへの逆マップ。
  * `idpool::IP`: ユニークなユニットID。
  * `timepool::TP`: ソートされたユニークな時間期間。
  * `laginds::Dict{Int, Vector{Int}}`: ラグ距離からラグ付き値のインデックスのベクトルへのマップ。
