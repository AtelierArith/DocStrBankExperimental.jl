```
MultiCoefplot
```

A `MultiCoefplot` object. It contains the all information for which a set of multiple `Coefplot`s should be plotted together. The keyword arguements of the constructor are all optional.

# Constructors

```julia
MultiCoefplot(data::Coefplot ...; <keyword arguments>)
```

# Arguments

  * `title::Label`: the title to the plot.
  * `xlabel::Label`: the xlabel to the plot.
  * `ylabel::Label`: the ylabel to the plot.
  * `xticklabel::CaptionStyle`: the style of the xtick.
  * `yticklabel::CaptionStyle`: the style of the ytick.
  * `legend::Legend`: the style of the legend.
  * `width::Real = 240`: the width of the axis frame
  * `height::Real = 204`: the height of the axis frame
  * `interval::Union{Real,Missing} = missing`: determines the distance between each `Coefplot`. Each `Coefplot`'s `offset` is computed according to this.
  * `sorter::Vector{String} = String[]`: a vector indicating the content and the order of the coefficients. If empty, use the union of the data.varname of each Coefplot.
  * `csorter::Vector{String} = String[]`: a vector indicating the order of the coefplots. If empty, use the order of data.
  * `note::Union{Note, Missing}`: a note that is attached to the south of the plot.
  * `vertical::Bool = true`: if `true`, the errorbars are parallel to y axis; if `false`, the errorbars are parallel to x axis.

The following arguements are from `Coefplots()`, and will be passed down to each `Coefplot` if specified in `MultiCoefplot()`.

  * `keepmark::Bool = true`: `true` if the user wants to plot the point estimates, `false` otherwise.
  * `keepconnect::Bool = false`: `true` if the user wants to connect the neighboring point estimates, `false` otherwise.
  * `mark::Mark`: the style of mark for the point estimates.
  * `errormark:Mark`: the style of mark for the endpoints of confidence interval.
  * `errorbar::Bar`: the style of the error bar.
  * `connect::Bar`: the style of the line that connects the neighboring point estimates.
  * `offset::Real = 0`: similar to that of the Stata package, it shifts the coefplot along the axis that represents coefficient name.
  * `sorter::Vector{String} = String[]`: a vector indicating the content and the order of the coefficients. If empty, use the order of the data.varname.
  * `level::Real = 0.95`: the confidence level.
