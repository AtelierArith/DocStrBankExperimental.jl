```
GridworldRenderer(; options...)
```

Customizable renderer for 2D gridworld domains.

# General options

  * `resolution::Tuple{Int64, Int64}`: Default figure resolution, in pixels.
  * `grid_fluents::Vector{Julog.Term}`: PDDL fluents that represent the grid layers (walls, etc).
  * `grid_colors::Vector`: Colors for each grid layer.
  * `has_agent::Bool`: Whether the domain has an agent not associated with a PDDL object.
  * `get_agent_x::Function`: Function that returns the PDDL fluent for the agent's x position.
  * `get_agent_y::Function`: Function that returns the PDDL fluent for the agent's y position.
  * `get_obj_x::Function`: Takes an object constant and returns the PDDL fluent for its x position.
  * `get_obj_y::Function`: Takes an object constant and returns the PDDL fluent for its y position.
  * `agent_renderer::Function`: Agent renderer, of the form `(domain, state) -> Graphic`.
  * `obj_renderers::Dict{Symbol, Function}`: Per-type object renderers, of the form `(domain, state, obj) -> Graphic`.
  * `obj_type_z_order::Vector{Symbol}`: Z-order for object types, from bottom to top.
  * `locations::Vector{Tuple}`: List of `(x, y, label, color)` tuples to label locations on the grid.
  * `show_inventory::Bool`: Whether to show an object inventory for each function in `inventory_fns`.
  * `inventory_fns::Vector{Function}`: Inventory indicator functions of the form `(domain, state, obj) -> Bool`.
  * `inventory_types::Vector{Symbol}`: Types of objects that can be each inventory.
  * `inventory_labels::Vector{String}`: Axis titles / labels for each inventory.
  * `inventory_labelsize::Real`: Inventory label font size.
  * `state_options::Dict{Symbol, Any}`: Default options for state rendering.
  * `trajectory_options::Dict{Symbol, Any}`: Default options for trajectory rendering.
  * `anim_options::Dict{Symbol, Any}`: Default options for animation rendering.

# State options

These options can be passed as keyword arguments to [`render_state`](@ref):

  * `show_grid::Bool = true`: Whether to show grid variables (walls, etc).
  * `show_agent::Bool = true`: Whether to show the agent.
  * `show_objects::Bool = true`: Whether to show objects.
  * `show_locations::Bool = true`: Whether to show locations.
  * `show_inventory::Bool = true`: Whether to show inventories.
  * `caption = nothing`: Caption to display below the figure.
  * `caption_font = :regular`: Font for the caption.
  * `caption_size = 24`: Font size for the caption.
  * `caption_color = :black`: Font color for the caption.
  * `caption_padding = 12`: Padding for the caption.
  * `caption_rotation = 0`: Rotation for the caption.

# Trajectory options

These options can be passed as keyword arguments to [`render_trajectory`](@ref):

  * `:agent_color = black`: Marker color of agent tracks.
  * `:agent_start_color = agent_color`: Marker color of agent tracks at the start   of the trajectory, which fade into the main color.
  * `:tracked_objects = Const[]`: Moving objects to plot marker tracks for.
  * `:object_colors = Symbol[]`: Marker colors to use for tracked objects.
  * `:object_start_colors = object_colors`: Marker colors to use for tracked   objects at the start of the trajectory, which fade into the main color.
  * `:tracked_types = Symbol[]`: Types of objects to track.
  * `:type_colors = Symbol[]`: Marker colors to use for tracked object types.
  * `:type_start_colors = type_colors`: Marker colors to use for tracked object   types at the start of the trajectory, which fade into the main color.
  * `:track_arrowmarker = '▶'`: Marker to use for directed tracks.
  * `:track_stopmarker = '⦿'`: Marker to use for stationary tracks.
  * `:track_markersize = 0.3`: Size of track markers.

# Animation options

These options can be passed as keyword arguments to animation functions:

  * `captions = nothing`: Captions to display for each timestep, e.g.,  `["t=1", "t=2", ...]`. Can be provided as a vector of strings, or a dictionary mapping timesteps to strings. If `nothing`, no captions are displayed.
  * `trail_length = 0`: Length of trail tracks to display for each agent or tracked object. If `0`, no trail tracks are displayed.
