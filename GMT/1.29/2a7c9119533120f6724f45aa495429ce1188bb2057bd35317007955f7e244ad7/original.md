```
radar(cmd0="", arg1=nothing; axeslimts=Float64[], annotall=false, axeslabels=String[], kwargs...)
```

Radar plots are a useful way for seeing which variables have similar values or if there are outliers amongst each variable. By default we expect a matrix, or a GMTdatset (or a vector of them) with normalized values. This is so because a radar plot has multiple axis that each have different limits. So the options are to pass normalized variables or set each axis limits via the `axeslimts` option.

  * `axeslimts`: A vector with the same size as columns in the input matrix with the max extent of each variable.              NOTE that if you don't provide this option we assume input data is normalized.
  * `annotall`: By default only the first axis is annotated, which is all it needs when variables are normalized.             However, when using non-normalized variables it may be useful to show the limits of each axis.
  * `axeslabels` or `labels`: String vector with the names of each variable axis. Plots a default "Label?" if                           not provided.

By default the polygons are not filled but that is often not so nice. To fill with the default cyclic color use just `fill=true`. Other options are to use:

  * `fill` or `fillcolor`: A string vector with polygon colors. If number of colors is less then number of                        polygons we cycle through the number of provided colors.
  * `fillalpha`: The default is to paint polygons with a transparency of 70%. For other transparency values              pass in a vector of transparencies (between [0-1] or ]1-100]) via this option.
  * `lw` or `pen`: Sets the outline pen settings (default is line thickness '= 1 pt' with same color as polygon's)

Examples:

```
radar([0.5 0.5 0.6 0.9 0.77; 0.6 0.5 0.8 0.2 0.9], show=true, marker=:circ, fill=true)

radar([10.5 20.5 30.6 40.9 46], axeslimts=[15, 25, 50, 90, 50], labels=["Spoons","Forks","Knifes","Dishes","Oranges"],
      annotall=true, marker=:circ, fill=true, show=1)
```
