```
asimage(dc::DiluvianCluster, colors::Vector{Colorant}, other = colorant"black")::Array{Colorant}
asimage(dc::DiluvianCluster)
```

Get a colorized image when the first `length(colors)` clusters are colored according to `colors` and the remainder are `other`. The second version uses `distinguishable_colors(…)` to generate the enough colors automatically.
