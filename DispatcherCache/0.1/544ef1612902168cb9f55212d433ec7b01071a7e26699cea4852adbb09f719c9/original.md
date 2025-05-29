```
add_hash_cache!(graph, endpoints=[], uncacheable=[]
                [; compression=DEFAULT_COMPRESSION, cachedir=DEFAULT_CACHE_DIR])
```

Optimizes a delayed execution graph `graph::DispatchGraph` by wrapping individual nodes in load-from-disk on execute-and-store wrappers depending on the state of the disk cache and of the graph. The function modifies inplace the input graph and should be called on the same unmodified `graph` after each execution and *not* on the modified graph.

Once the original graph is modified, calling `run!` on it will, if the cache is already present, load the top most consistent key or alternatively re-run and store the outputs of nodes which have new state.

# Arguments

  * `exec::Executor` the `Dispatcher.jl` executor
  * `graph::DispatchGraph` input dispatch graph
  * `endpoints::AbstractVector` leaf nodes for which caching will occur;

nodes that depend on these will not be cached. The nodes can be specified either by label of by the node object itself

  * uncacheable::AbstractVector` nodes that will never be cached and

will always be executed (these nodes are still hashed and their hashes influence upstream node hashes as well)

# Keyword arguments

  * `compression::String` enables compression of the node outputs.

Available options are `"none"`, for no compression, `"bz2"` or `"bzip2"` for BZIP compression and `"gz"` or `"gzip"` for GZIP compression

  * `cachedir::String` the cache directory.

Note: This function should be used with care as it modifies the input       dispatch graph. One way to handle this is to make a function that       generates the dispatch graph and calling `add_hash_cache!` each time on       the distict, functionally identical graphs.
