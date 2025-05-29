```
BlocksworldRenderer(; options...)
```

Specialization of [`GraphworldRenderer`](@ref) for the blocksworld domain, which  uses a custom [`BlocksworldLayout`](@ref) and default renderers for blocks and tables. The following blocksworld-specific options are supported:

# Options

  * `block_type::Symbol`: PDDL type of blocks, defaults to `:block`
  * `block_width::Real`: Width of blocks, defaults to `1.0`
  * `block_height::Real`: Height of blocks, defaults to `1.0`
  * `block_gap::Real`: Gap between blocks, defaults to `0.5`
  * `table_height::Real`: Height of table, defaults to `block_height`
  * `gripper_height::Real`: Height of blocks when they are picked up. Defaults    to slightly above the tallest block tower.
  * `block_colors`: Colorscheme for blocks, defaults to a discretization of the   `plasma` colorscheme.
  * `block_renderer`: Renderer for blocks, defaults to a colored square with the   block name as white text in the center.
