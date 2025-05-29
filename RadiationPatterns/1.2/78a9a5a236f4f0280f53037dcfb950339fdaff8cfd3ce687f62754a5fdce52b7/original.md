ptn_2d(     Pat::Union{Pattern,Vector{<:Pattern}};     ind::Union{Int,Vector{Int}} = 1,     dims::Union{Int,Vector{Int}} = 1,     type::String = "normal",     xlabel::String = "",     ylabel::String = "",     xrange::Vector{<:Real} = [0, 0],     yrange::Vector{<:Real} = [0, 0],     trange::Vector{<:Real} = [0, 0],     rrange::Vector{<:Real} = [0, 0],     width::Real = 0,     height::Real  = 0,     mode::Union{String,Vector{String}} = "lines",     color::Union{String,Vector{String}} = "",     name::Union{String,Vector{String}}  = "", )

Plots a 2D radiation pattern by setting the keywords `ind` and `dim`. For example, setting `dim=1` takes the slice of `U[:, ind]`, and setting `dim=2` takes the slice of `U[ind, :]`. Can be used for comparing two or more patterns also (see the example `ex_basics.jl` and `ex_horn.jl`). When comparing two or more pattern cuts, one can specify different `ind`, `dims`, `mode`, `color` and `name` by setting these keywords as vectors (if not set, default values are used).

#### Arguments

  * `Pat`: A `Pattern` or a vector of `Pattern`s
  * `ind`: Index to slice the pattern (default: `1`)
  * `dims`: Dimension to slice the pattern, either `1` or `2` (default: `1`)
  * `type`: Plot type, either `"normal"` or `"polar"` (default: `"normal"`)
  * `xlabel`: Label for the x-axis (default: `""`)
  * `ylabel`: Label for the y-axis (default: `""`)
  * `xrange`: Range for the x-axis (default: `[0, 0]`)
  * `yrange`: Range for the y-axis (default: `[0, 0]`)
  * `trange`: Range for the angular axis (default: `[0, 0]`)
  * `rrange`: Range for the radial axis (default: `[0, 0]`)
  * `width`: Width of the plot (default: `0`)
  * `height`: Height of the plot (default: `0`)
  * `mode`: Plotting mode (default: `"lines"`)
  * `color`: Color of the plot lines (default: `""`)
  * `name`: Name of the plot lines (default: `""`)
