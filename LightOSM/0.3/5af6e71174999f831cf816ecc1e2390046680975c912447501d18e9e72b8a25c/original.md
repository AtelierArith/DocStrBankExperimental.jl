OpenStreetMap building.

# Fields

`T<:String`

  * `id::T`: OpenStreetMap building way id a simple polygon, relation id if a multi-polygon
  * `is_relation::Bool`: True if building is a a multi-polygon / relation.
  * `polygons::Vector{Polygon{T}}`: List of building polygons, first is always the outer ring.
  * `tags::AbstractDict{String,Any}`: Metadata tags.
