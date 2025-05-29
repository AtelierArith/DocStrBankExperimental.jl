```
GroupedCoefplot
```

A `GroupedCoefplot` object. It contains the all information for which a grouoped coefplot should be plotted. The keyword arguements of the constructors are all optional.

# Constructors

```julia
GroupedCoefplot(data::Pair{<:Any, Coefplot}...;  <keyword arguments>)
GroupedCoefplot(gdata::GroupedDataFrame;  <keyword arguments>)
```

# Arguments

  * `title::Label`: the title to the plot.
  * `xlabel::Label`: the xlabel to the plot.
  * `ylabel::Label`: the ylabel to the plot.
  * `xticklabel::CaptionStyle`: the style of the xtick.
  * `yticklabel::CaptionStyle`: the style of the ytick.
  * `width::Real = 240`: the width of the axis frame
  * `height::Real = 204`: the height of the axis frame
  * `note::Union{Note, Missing}`: a note that is attached to the south of the plot.
  * `vertical::Bool = true`: if `true`, the errorbars are parallel to y axis; if `false`, the errorbars are parallel to x axis.
