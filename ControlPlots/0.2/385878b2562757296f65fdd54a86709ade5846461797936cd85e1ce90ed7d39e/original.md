```
plot(X, Ys::AbstractVector{<:Union{AbstractVector, Tuple}}; xlabel="", ylabel="",
labels=nothing, xlims=nothing, ylims=nothing, ann=nothing, scatter=false, 
title="", fig="", ysize=14, disp=false)
```

Plot multiple curves given by `Ys` against a common x-axis `X`.

# Arguments

  * `X`: The x-axis values.
  * `Ys`: A vector of vectors representing the y-axis values for each curve.

# Optional Arguments

  * `xlabel`: The label for the x-axis. Default is an empty string.
  * `ylabel`: The label for the y-axis. Default is an empty string.
  * `labels`: The labels for each curve. Default is `nothing`.
  * `xlims`: The limits for the x-axis. Default is `nothing`.
  * `ylims`: The limits for the y-axis. Default is `nothing`.
  * `ann`: An annotation to be placed on the plot. Default is `nothing`.
  * `scatter`: A boolean indicating whether to plot the points as a scatter plot. Default is `false`.
  * `title`: The title of the figure. Default is an empty string.
  * `fig`: The name of the figure. Default is an empty string.
  * `ysize`: The font size for the y-axis label. Default is 14.
  * `disp`: A boolean indicating whether to display the plot. If false, only create a structure to be displayed later.          Default is `false`.
