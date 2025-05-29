```
Edge(source::UInt, target::UInt, type::AbstractString, properties::Config)
```

Represents an edge in the property graph.

# Fields

  * `source::UInt`: The unique identifier of the source node.
  * `target::UInt`: The unique identifier of the target node.
  * `type::AbstractString`: The type or label of the edge.
  * `properties::Config`: A `Config` object representing the properties (key-value pairs) associated with the edge.

# Constructors

  * `Edge(src::Integer, tgt::Integer, type::AbstractString; props...)`: Convenience constructor to create an `Edge` with the given `src` and `tgt` node IDs (converted to `UInt`), `type`, and optional `props` which are passed to the `Config` constructor.
  * `Edge(src::UInt, tgt::UInt, type::AbstractString; props...)`: Convenience constructor to create an `Edge` with the given `src` and `tgt` node IDs, `type`, and optional `props` which are passed to the `Config` constructor.

# Examples

```julia
Edge(1, 2, "friend"; since=2010)
```
