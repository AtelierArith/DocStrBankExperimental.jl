```
D3Tree(node; detect_repeat=true, lazy_expand_after_depth=typemax(Int), kwargs...)
```

Construct a tree to be displayed using D3 in a browser or ipython notebook with any object, `node`, that implements the AbstractTrees interface. 

The style may be controlled by implementing the following functions, which should return `String`s for the nodes:

```@docs
D3Trees.text(node)
D3Trees.tooltip(node)
D3Trees.style(node)
D3Trees.link_style(node)
```

Allows for lazy loading of large trees through the `lazy_expand_after_depth` keyword argument. Nodes beyonnd this depth are not intially expanded for visualization.  Instead, they are cached and only expanded when requested by the visualization. The serving is done by the D3Trees HTTP server.

The server does not have information about the lifetime of different visualizations so it might keep references to past visualizations,  potentially holding up a lot of memory. To reset the server and remove references to old data, run either `D3Trees.reset_server()` or `D3Trees.shutdown_server()`.

# Arguments

## Required

  * `node`: an object that has AbstractTrees.children(node) and AbstractTrees.printnode(io::IO, node)

## Keyword

  * `detect_repeat`: (default: true) if true, uses a dictionary to detect whether a node has appeared previously
  * `lazy_expand_after_depth::Integer`: (default: typemax(Int)). Sets tree depth to at which `AbstractTrees.children(node)` will not be called anymore. Instead, nodes at this depth are cached and `children(node)` is called only when node is clicked in the D3 interactive visualization. Root has depth 0, so setting `lazy_expand_after_depth=1` expands only the root.
  * `lazy_subtree_depth::Integer`: (default: 2) sets depth of subtrees fetched from D3Trees server
  * `port::Integer`: (default: 16370) specify server port for D3Trees server that will serve subtrees for visualization. Shutdown server by `shutdown_server(port)`.
  * `dry_run_lazy_vizualization::Function`: (default: t -> D3Trees.dry*run*server(port, t)) function that is ran once before visualization is started to speed up first fetch in the visualization. Provide custom function if your tree's children method takes a long time on first run.
  * Also supports, the non-vector arguments of the vector-of-vectors `D3Tree` constructor, i.e. `title`, `init_expand`, `init_duration`, `svg_height`.
