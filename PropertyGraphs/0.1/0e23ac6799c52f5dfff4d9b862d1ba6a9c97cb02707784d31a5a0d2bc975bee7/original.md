```
Node(id::UInt, labels::Vector{String}, properties::Config) <: AbstractNodeLike
```

Represents a node in the property graph. 

# Fields

  * `id::UInt`: The unique identifier for the node.
  * `labels::Vector{String}`: A vector of labels associated with the node. Labels are used to group or categorize nodes.
  * `properties::Config`: A `Config` object representing the properties (key-value pairs) associated with the node.

# Constructors

  * `Node(id::UInt, labels::AbstractString...; props...)`: Convenience constructor to create a `Node` with the given `id`, one or more `labels`, and optional `props` which are passed to the `Config` constructor.

# Examples

```julia
Node(1, :person, :human, name="John Doe", age=25)
```
