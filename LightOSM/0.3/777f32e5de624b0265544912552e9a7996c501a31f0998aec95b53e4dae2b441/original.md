OpenStreetMap turn restriction (relation).

# Fields

`T<:String`

  * `id::T`: OpenStreetMap relation id.
  * `type::String`: Either a `via_way` or `via_node` turn restriction.
  * `tags::AbstractDict{String,Any}`: Metadata tags.
  * `from_way::T`: Incoming way id to the turn restriction.
  * `to_way::T`: Outgoing way id to the turn restriction.
  * `via_node::Union{T,Nothing}`: Node id at the centre of the turn restriction.
  * `via_way::Union{Vector{T},Nothing}`: Way id at the centre of the turn restriction.
  * `is_exclusion::Bool`: Turn restrictions such as `no_left_turn`, `no_right_turn` or `no_u_turn`.
  * `is_exclusive::Bool`: Turn restrictions such as `striaght_on_only`, `left_turn_only`, `right_turn_only`.
