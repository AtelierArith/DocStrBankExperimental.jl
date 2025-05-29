```
multiternary(dc::DiluvianCluster, cluster::Int; maxitems=1000, norm=1.0, palette = nothing, variance = false)
```

Plot the data from the specified cluster from most significant dimensions as ternary diagram. `maxitems` limits the total number of points plotted when there are a very large number of data points. `norm` is useful if the data is normalized to something other than unity. `palette` defaults to the same default palette as toimage(…) or can be specified as `Colorant[]` `variance` determines whether maximum mean value or maximum variance is used to select elements to plot
