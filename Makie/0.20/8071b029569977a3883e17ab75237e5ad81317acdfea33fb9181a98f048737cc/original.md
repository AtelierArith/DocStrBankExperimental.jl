```
series(curves;
    linewidth=2,
    color=:lighttest,
    solid_color=nothing,
    labels=nothing,
    # scatter arguments, if any is set != nothing, a scatterplot is added
    marker=nothing,
    markersize=nothing,
    markercolor=automatic,
    strokecolor=nothing,
    strokewidth=nothing)
```

Curves can be:

  * `AbstractVector{<: AbstractVector{<: Point2}}`: the native representation of a series as a vector of lines
  * `AbstractMatrix`: each row represents y coordinates of the line, while `x` goes from `1:size(curves, 1)`
  * `AbstractVector, AbstractMatrix`: the same as the above, but the first argument sets the x values for all lines
  * `AbstractVector{<: Tuple{X<: AbstractVector, Y<: AbstractVector}}`: A vector of tuples, where each tuple contains a vector for the x and y coordinates
