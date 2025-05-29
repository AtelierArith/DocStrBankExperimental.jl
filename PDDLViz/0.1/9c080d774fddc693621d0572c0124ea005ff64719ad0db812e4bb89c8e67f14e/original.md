```
GraphworldRenderer(; options...)
```

Customizable renderer for domains with fixed locations and movable objects connected in a graph. The layout of the graph can be controlled with the `graph_layout` option, which takes a function that returns an `AbstractLayout` given the number of locations.

By default, the graph is laid out using the `StressLocSpringMov` layout, which  arranges the first `n_locs` nodes via stress minimization, and uses spring/repulsion for the remaining nodes.

# General options

  * `resolution::Tuple{Int64, Int64}`: Default figure resolution, in pixels.
  * `graph_layout::Function`: Function `n_locs -> (graph -> positions)` that returns an AbstractLayout.
  * `is_loc_directed::Bool`: Whether the edges between locations are directed.
  * `is_mov_directed::Bool`: Whether the edges between movable objects are directed.
  * `has_mov_edges::Bool`: Whether there are edges between movable objects.
  * `locations::Vector{Julog.Const}`: PDDL objects that correspond to fixed locations.
  * `location_types::Vector{Symbol}`: PDDL object types that correspond to fixed locations.
  * `movables::Vector{Julog.Const}`: PDDL objects that correspond to movable objects.
  * `movable_types::Vector{Symbol}`: PDDL object types that correspond to movable objects.
  * `loc_edge_fn::Function`: Function `(dom, s, l1, l2) -> Bool` that checks if `l1` connects to `l2`.
  * `loc_edge_label_fn::Function`: Function `(dom, s, l1, l2) -> String` that labels edge `(l1, l2)`.
  * `mov_loc_edge_fn::Function`: Function `(dom, s, obj, loc) -> Bool` that checks if `mov` is at `loc`.
  * `mov_loc_edge_label_fn::Function`: Function `(dom, s, obj, loc) -> String` that labels edge `(mov, loc)`.
  * `mov_edge_fn::Function`: Function `(dom, s, m1, m2) -> Bool` that checks if `m1` connects to `m2`.
  * `mov_edge_label_fn::Function`: Function `(dom, s, m1, m2) -> String` that labels edge `(m1, m2)`.
  * `loc_renderers::Dict{Julog.Const, Function}`: Location object renderers, of the form `(domain, state, loc) -> Graphic`.
  * `mov_renderers::Dict{Julog.Const, Function}`: Movable object renderers, of the form `(domain, state, obj) -> Graphic`.
  * `loc_type_renderers::Dict{Symbol, Function}`: Per-type location renderers, of the form `(domain, state, loc) -> Graphic`.
  * `mov_type_renderers::Dict{Symbol, Function}`: Per-type movable renderers, of the form `(domain, state, obj) -> Graphic`.
  * `graph_options::Dict{Symbol, Any}`: Default options for graph rendering, passed to the `graphplot` recipe.
  * `axis_options::Dict{Symbol, Any}`: Default display options for axis.
  * `state_options::Dict{Symbol, Any}`: Default options for state rendering.
  * `anim_options::Dict{Symbol, Any}`: Default options for animation rendering.

# State options

These options can be passed as keyword arguments to [`render_state`](@ref):

  * `show_location_graphics = true`: Whether to show location graphics.
  * `show_location_labels = true`: Whether to show location labels.
  * `show_movable_graphics = true`: Whether to show movable object graphics.
  * `show_movable_labels = true`: Whether to show movable object labels.
  * `show_edge_labels = false`: Whether to show edge labels.
  * `location_node_color = :black`: Color of location nodes.
  * `location_edge_color = :black`: Color of edges between locations.
  * `movable_node_color = :gray`: Color of movable object nodes.
  * `movable_edge_color = (:mediumpurple, 0.75)`: Color of edges between locations and movable objects.
  * `label_offset = 0.15`: How much labels are offset from the center of their corresponding objects. Larger values move the labels further away.
