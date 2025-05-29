OpenStreetMap ビルディング。

# フィールド

`T<:String`

  * `id::T`: OpenStreetMap ビルディングウェイの ID、単純ポリゴンの場合は、マルチポリゴンの場合はリレーション ID。
  * `is_relation::Bool`: ビルディングがマルチポリゴン / リレーションの場合は True。
  * `polygons::Vector{Polygon{T}}`: ビルディングポリゴンのリスト、最初のものは常に外側のリング。
  * `tags::AbstractDict{String,Any}`: メタデータタグ。
