OpenStreetMap way.

# Fields

`T<:Integer`

  * `id::T`: OpenStreetMap way id.
  * `nodes::Vector{T}`: Ordered list of node ids making up the way.
  * `tags::AbstractDict{String,Any}`: Metadata tags.
