```
GroupedMultiCoefplot
```

A `GroupedMultiCoefplot` object. It contains the all information for which a set of multiple `GroupedCoefplot`s should be plotted together. The keyword arguements of the constructor are all optional.

# Constructors

```julia
GroupedMultiCoefplot(data::Pair{<:Any, GroupedCoefplot} ...;  <keyword arguments>)
GroupedMultiCoefplot(data::Pair{<:Any, MultiCoefplot} ...;  <keyword arguments>)
```

# Arguments

  * `title::Label`: the title to the plot.
  * `xlabel::Label`: the xlabel to the plot.
  * `ylabel::Label`: the ylabel to the plot.
  * `xticklabel::CaptionStyle`: the style of the xtick.
  * `yticklabel::CaptionStyle`: the style of the ytick.
  * `show_legend::Union{Vector{Bool}, Missing} = missing`: a boolean vector specifying which legend of the subplot should be shown. The default is to show only the first legend.
  * `width::Real = 240`: the width of the axis frame
  * `height::Real = 204`: the height of the axis frame
  * `interval::Union{Real,Missing} = missing`: determines the distance between each `Coefplot`. Each `Coefplot`'s `offset` is computed according to this.
  * `note::Union{Note, Missing}`: a note that is attached to the south of the plot.
  * `vertical::Bool = true`: if `true`, the errorbars are parallel to y axis; if `false`, the errorbars are parallel to x axis.
