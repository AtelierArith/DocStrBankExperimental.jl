OpenStreetMapのターン制限（リレーション）。

# フィールド

`T<:String`

  * `id::T`: OpenStreetMapリレーションID。
  * `type::String`: `via_way`または`via_node`のいずれかのターン制限。
  * `tags::AbstractDict{String,Any}`: メタデータタグ。
  * `from_way::T`: ターン制限への進入ウェイID。
  * `to_way::T`: ターン制限からの出発ウェイID。
  * `via_node::Union{T,Nothing}`: ターン制限の中心にあるノードID。
  * `via_way::Union{Vector{T},Nothing}`: ターン制限の中心にあるウェイID。
  * `is_exclusion::Bool`: `no_left_turn`、`no_right_turn`、または`no_u_turn`のようなターン制限。
  * `is_exclusive::Bool`: `straight_on_only`、`left_turn_only`、`right_turn_only`のようなターン制限。
