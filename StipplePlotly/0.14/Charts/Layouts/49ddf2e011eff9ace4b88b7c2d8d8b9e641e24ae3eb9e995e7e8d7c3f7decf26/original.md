```
PlotLayoutGrid()
```

---

# Examples

---

```
julia>
```

---

# Properties

---

  * `columns::String` - The number of columns in the grid. If you provide a 2D `subplots` array, the length of its longest row is used as the default. If you give an `xaxes` array, its length is used as the default. But it's also possible to have a different length, if you want to leave a row at the end for non-cartesian subplots. Type: integer greater than or equal to `1`
  * `domain_x::Vector{Float64}` - Sets the horizontal domain of this grid subplot (in plot fraction). The first and last cells end exactly at the domain edges, with no grout around the edges. Default: `[0, 1]`
  * `domain_y::Vector{Float64}` - Sets the vertical domain of this grid subplot (in plot fraction). The first and last cells end exactly at the domain edges, with no grout around the edges. Default: `[0, 1]`
  * `pattern::String` - If no `subplots`, `xaxes`, or `yaxes` are given but we do have `rows` and `columns`, we can generate defaults using consecutive axis IDs, in two ways: "coupled" gives one x axis per column and one y axis per row. "independent" uses a new xy pair for each cell, left-to-right across each row then iterating rows according to `roworder`. Type: one of `"coupled"` or `"independent"` | Default. `"coupled"`
  * `roworder::String` - Is the first row the top or the bottom? Note that columns are always enumerated from left to right. enumerated , one of ( `"top to bottom"` | `"bottom to top"` ) | Default: `"top to bottom"`
  * `rows::Int` - The number of rows in the grid. If you provide a 2D `subplots` array or a `yaxes` array, its length is used as the default. But it's also possible to have a different length, if you want to leave a row at the end for non-cartesian subplots. Type: integer greater than or equal to `1`
  * `subplots::Matrix{String}` - Used for freeform grids, where some axes may be shared across subplots but others are not. Each entry should be a cartesian subplot id, like "xy" or "x3y2", or "" to leave that cell empty. You may reuse x axes within the same column, and y axes within the same row. Non-cartesian subplots and traces that support `domain` can place themselves in this grid separately using the `gridcell` attribute.
  * `xaxes::Vector{String}` - Used with `yaxes` when the x and y axes are shared across columns and rows. Each entry should be an x axis id like "x", "x2", etc., or "" to not put an x axis in that column. Entries other than "" must be unique. Ignored if `subplots` is present. If missing but `yaxes` is present, will generate consecutive IDs.
  * `xgap::Float64` - Horizontal space between grid cells, expressed as a fraction of the total width available to one cell. Defaults to 0.1 for coupled-axes grids and 0.2 for independent grids.  Type: number between or equal to `0` and `1`
  * `xside::String` - Sets where the x axis labels and titles go. "bottom" means the very bottom of the grid. "bottom plot" is the lowest plot that each x axis is used in. "top" and "top plot" are similar.  Type: enumerated , one of ( `"bottom"` | `"bottom plot"` | `"top plot"` | `"top"` )  | Default: `"bottom plot"`
  * `yaxes::Vector{String}` - Used with `yaxes` when the x and y axes are shared across columns and rows. Each entry should be an y axis id like "y", "y2", etc., or "" to not put a y axis in that row. Entries other than "" must be unique. Ignored if `subplots` is present. If missing but `xaxes` is present, will generate consecutive IDs.
  * `ygap::Float64` - Vertical space between grid cells, expressed as a fraction of the total height available to one cell. Defaults to 0.1 for coupled-axes grids and 0.3 for independent grids. Type: number between or equal to `0` and `1`
  * `yside::String` - Sets where the y axis labels and titles go. "left" means the very left edge of the grid. "left plot" is the leftmost plot that each y axis is used in. "right" and "right plot" are similar. Type: enumerated , one of ( `"left"` | `"left plot"` | `"right plot"` | `"right"` ) | Default: `"left plot"`
