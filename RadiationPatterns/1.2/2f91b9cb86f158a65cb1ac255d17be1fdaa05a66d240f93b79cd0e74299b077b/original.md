ptn*holo(     Pat::Pattern;     xlabel::String = "",     ylabel::String = "",     zrange::Vector{<:Real} = [0, 0],     ref*size = 500,     colorscale = "Jet", )

Plots a holographic (heatmap) radiation pattern. Currently I have issues in setting both the axis ratio and the range of the heatmap plot. In order to have an 1:1 aspect ratio, I have tried to fine tune the width and height of the plot. One can try to adjust the `ref_size` keyword to set the figure size. I hope that more improvements can be made in the future.

#### Arguments

  * `Pat`: A `Pattern`
  * `xlabel`: Label for the x-axis (default: `""`)
  * `ylabel`: Label for the y-axis (default: `""`)
  * `zrange`: Range for the z-axis (default: `[0, 0]`)
  * `ref_size`: ref size of the plot in pixels (default: `500`)
  * `colorscale`: Color scale for the heatmap (default: `"Jet"`)
