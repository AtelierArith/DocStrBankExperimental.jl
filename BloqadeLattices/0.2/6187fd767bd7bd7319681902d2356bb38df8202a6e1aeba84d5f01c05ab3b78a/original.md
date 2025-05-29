```
img_atoms(atoms::Union{AtomList, BoundedLattice};
        colors = [DEFAULT_LINE_COLOR[], ...],
        texts = ["1", "2", ...],
        vectors = [],
        format = :svg,
        filename = nothing,
        kwargs...
    )
```

Plots `atoms` or `bounded_lattice.site_positions` with colors specified by `colors` and texts specified by `texts`. You will need a `VSCode`, `Pluto` notebook or `Jupyter` notebook to show the image. If you want to write this image to the disk without displaying it in a frontend, please try

```julia
julia> img_atoms(generate_sites(SquareLattice(), 5, 5); filename="test.png")
```

### Keyword Arguments

##### features

  * `colors` is a vector of colors for nodes
  * `texts` is a vector of string displayed on nodes
  * `vectors` is a vector of (start*loc, end*loc) pair to specify a list of arrows.

##### IO

  * `format` can be `:svg`, `:pdf` or `:png`
  * `filename` can be a filename string with suffix `.svg`, `.png` or `.pdf`

##### general

  * `background_color = DEFAULT_BACKGROUND_COLOR[]`
  * `scale::Int = 60.0` is the number of pixels per unit length
  * `xpad::Float64 = 2.5` is the padding space in x axis
  * `ypad::Float64 = 1.5` is the padding space in y axis

##### axes

  * `axes_text_color = DEFAULT_TEXT_COLOR[]`
  * `axes_text_fontsize::Float64 = 16.0`
  * `axes_num_of_xticks = 5`
  * `axes_num_of_yticks = 5`
  * `axes_x_offset::Float64 = 0.5`
  * `axes_y_offset::Float64 = 0.5`
  * `axes_unit::String = "μm"`

##### node

  * `node_text_fontsize::Float64 = 16.0`
  * `node_text_color = DEFAULT_TEXT_COLOR[]`
  * `node_stroke_color = DEFAULT_LINE_COLOR[]`
  * `node_stroke_linewidth = 1`
  * `node_fill_color = DEFAULT_NODE_COLOR[]`

##### bond

  * `bond_color = DEFAULT_LINE_COLOR[]`
  * `bond_linewidth::Float64 = 1.0`

##### blockade

  * `blockade_radius::Float64=0`, atoms within `blockade_radius` will be connected by edges.
  * `blockade_style::String = "none"`, can be "none" or "dashed"
  * `blockade_stroke_color = DEFAULT_LINE_COLOR[]`
  * `blockade_fill_color = "transparent"`
  * `blockade_fill_opacity::Float64 = 0.5`
  * `blockade_stroke_linewidth = 1.0`   # in pt

##### arrow

  * `arrow_linewidth`
  * `arrow_color`
  * `arrow_head_length`

##### grid

  * `grid_stroke_color="#AAAAAA"`
  * `grid_stroke_width::Float64=1`
  * `grid_stroke_style::String="dashed"`
