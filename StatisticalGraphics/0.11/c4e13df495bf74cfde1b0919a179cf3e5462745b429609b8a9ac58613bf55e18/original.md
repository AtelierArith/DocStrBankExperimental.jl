```
sgplot(ds, plots;
                mapformats=true,
                nominal=nothing,
                xaxis=Axis(),
                x2axis=Axis(),
                yaxis=Axis(),
                y2axis=Axis(),
                legend=true,
                threads=automatic,
                opts...)
```

Produce a statistical graphics. The `ds` argument is referring to a data set (or grouped data set) and `plots` is a vector of marks, such as Bar, Pie,.... 

The `opts...` refers to extra keyword arguments which can be passed to `sgplot`. These keywords depend depend whether `ds` is a data set or a grouped data set. Below shows the available keyword arguments for each case.

# Non-grouped data sets

# Keyword arguments

## Plot appearance

  * `backcolor`: The backgroud color for whole graph. default: `:white`
  * `clip`: The clip option for whole plot. default: `true`
  * `font`: The default font. default: `"sans-serif"`
  * `fontweight`: The font weight value. default: `400`
  * `groupcolormodel`: The color model to be used when `group` is used for specific plot. default: `:category`
  * `height`: The width of plot. default: `400`
  * `italic`: The default value whether the package use italic fonts. default: `false`
  * `wallcolor`: The backgroud color for plot area. default: `:transparent`
  * `width`: The width of plot. default: `600`

# Grouped data sets
