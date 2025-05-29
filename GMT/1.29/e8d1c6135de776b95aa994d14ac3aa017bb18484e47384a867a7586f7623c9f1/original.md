```
boxplot(data, grp=[]; pos=nothing, kwargs...)
```

  * `data`: A vector (plots a single box), a Matrix (plots n columns boxes), a MxNxG (plots `G` groups)         of `N` columns boxes, a Vector{Vector} (plots n clumn boxes but from data of different sizes),         a Vector{Vector{Vector}} (plots G groups - length(data) -, where groups may have variable number         of elements and each have its own size.)
  * `grp`: Categorical vector (made of integers or text strings) used to break down a the data column vector        in cathegories (groups).
  * `pos`: a coordinate vector (or a single location when `data` is a vector) where to plot the boxes.         Default plots them at 1:n*boxes or 1:n*groups.
  * `ccolor`: Logical value indicating whether the groups have constant color (when `fill=true` is used)          or have variable color (the default).
  * `fill`: If fill=true paint the boxes with a pre-defined color scheme. Otherwise, give a list of colors         to paint the boxes.
  * `fillalpha` : When `fill` option is used, we can set the transparency of filled boxes with this         option that takes in an array (vec or 1-row matrix) with numeric values between [0-1] or ]1-100],

```
      where 100 (or 1) means full transparency.
```

  * `boxwidth` or `cap`: Sets the the boxplot width and, optionally, the cap width. Provide info as         `boxwidth="10p/3p"` to set the boxwidth different from the cap's. Note, however, that this          requires GMT6.5. Previous versions do not destinguish box and cap widths.
  * `groupWidth`: Specify the proportion of the x-axis interval across which each x-group of boxes should          be spread. The default is 0.75.
  * `notch`: Logical value indicating whether the box should have a notch.
  * `outliers`: If other than a NamedTuple, plots outliers (1.5IQR) with the default black 5pt stars.             If argument is a NamedTuple (marker=??, size=??, color=??, markeredge=??), where `marker`             is one of the `plots` marker symbols, plots the outliers with those specifications. Any missing             spec default to the above values. i.e `outliers=(size="3p")` plots black 3 pt stars.
  * `horizontal` or `hbar`: plot horizontal instead of vertical boxplots.
  * `weights`: Array giving the weights for the data in `data`. The array must be the same size as `data`.
  * `region` or `limits`: By default we estimate the plotting limits but sometimes that may not be convenient.          Give a region=(x*min,x*max,y*min,y*max) tuple if you want to control the plotting limits.
  * `separator`: If = true plot a black line separating the groups. Otherwise provide the pen settings of those lines.
  * `ticks` or `xticks` or `yticks`: A tuple with annotations interval and labels. E.g. xticks=(1:5, ["a", "b", "c", "d"])          where first element is an AbstractArray and second an array or tuple of strings or symbols.
