OpenStreetMap ウェイ。

# フィールド

`T<:Integer`

  * `id::T`: OpenStreetMap ウェイの ID。
  * `nodes::Vector{T}`: ウェイを構成するノード ID の順序付きリスト。
  * `tags::AbstractDict{String,Any}`: メタデータタグ。
