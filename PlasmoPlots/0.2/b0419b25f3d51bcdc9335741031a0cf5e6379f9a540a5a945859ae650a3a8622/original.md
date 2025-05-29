```
PlasmoPlots.layout_plot(
    graph::OptiGraph,
    subgraphs::Vector{OptiGraph};
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

Plot a graph layout of the optigraph `graph` where `subgraphs` can contain overlapping nodes. Nodes that overlap are displayed as larger markers.
