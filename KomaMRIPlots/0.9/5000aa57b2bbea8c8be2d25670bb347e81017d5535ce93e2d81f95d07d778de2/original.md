```
p = plot_image(image; height, width, zmin, zmax, darkmode, title)
```

Plots an image matrix.

# Arguments

  * `image`: (`::Matrix{Number}`) image matrix

# Keywords

  * `width`: (`::Integer`, `=nothing`) plot width
  * `height`: (`::Integer`, `=nothing`) plot height
  * `zmin`: (`::Real`, `=minimum(abs.(image[:]))`) reference value for minimum color
  * `zmax`: (`::Real`, `=maximum(abs.(image[:]))`) reference value for maximum color
  * `darkmode`: (`::Bool`, `=false`) boolean to indicate whether to display darkmode style
  * `title`: (`::String`, `=""`) plot title

# Returns

  * `p`: (`::PlotlyJS.SyncPlot`) plot of the image matrix
