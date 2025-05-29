```
PlasmoPlots.layout_plot(
    graph::OptiGraph; 
    node_labels=false, 
    subgraph_colors=false, 
    node_colors=false, 
    linewidth=2.0,
    linealpha=1.0, 
    markersize=30,
    labelsize=20, 
    markercolor=:grey,
    layout_options = Dict(
        :tol => 0.01,
        :C => 2,
        :K => 4, 
        :iterations => 2
    ),
    plt_options = Dict(
        :legend => false,
        :framestyle => :box,
        :grid => false,
        :size => (800,800),
        :axis => nothing
    ),
    line_options = Dict(
        :linecolor => :blue,
        :linewidth => linewidth,
        :linealpha => linealpha)
    )
)
```

Plot a graph layout of the optigraph `graph`. The following keyword arguments can be provided to customize the graph layout.

  * `node_labels = false`: whether to label nodes using the corresponding optinode label attribute.
  * `subgraph_colors = false`: whether to color nodes according to their subgraph.
  * `node_colors = false`: whether to color nodes.  Only active if `subgraph_colors = false`.
  * `linewidth = 2.0`: the linewidth attribute for each edge in `graph`.
  * `linealpha = 1.0`: the linealpha attribute for each edge in `graph`.
  * `markersize = 30`: the markersize which determines the size of each node in `graph`.
  * `labelsize = 20`: the size for each node label.  Only active if `node_labels = true`.
  * `markercolor = :grey`: the color for each node.
  * `layout_options = Dict(:tol => 0.01,:C => 2, :K => 4, :iterations => 2)`: dictionary with options for the layout algorithm.

      * `tol`: permitted distance between a current and calculated co-ordinate.
      * `C`,`K`: scaling parameters.
      * `iterations`: number of iterations used to apply forces.
  * `plt_options = Dict(:legend => false,:framestyle => :box,:grid => false,:size => (800,800),:axis => nothing)`: dictionary with primary plotting options.

      * `legend`: whether to include legend, or legend position.
      * `framestyle`: style of frame used for plot.
      * `size`: size of the resulting plot.
      * `axis`: whether to include the axis.  The axis typically does not make sense for a graph layout plot.
      * It is also possible to use various plotting options compatible with `Plots.scatter` from the `Plots.jl` package.
  * `line_options = Dict(:linecolor => :blue,:linewidth => linewidth,:linealpha => linealpha)`: line plotting options used to display edges in the graph.

      * `linecolor`: color to use for each line.
      * `linewidth`: linewidth to use for each edge.  Defaults to the above option.
      * `linealpha`: linealpha to use for each edge. Default to the above option.
