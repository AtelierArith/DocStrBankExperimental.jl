```julia
struct Context{T}
```

Context is a container for storing any contextual information. It uses Memento pattern to keep track of prior history.  While the context can be changed, explict save/restore can be used to save the current context and restore the most recently saved one.

# Fields

  * `id::UInt64`: ID of the context
  * `history::DataStructures.Stack`: History of context data
  * `path::Vector{Symbol}`: Call path
