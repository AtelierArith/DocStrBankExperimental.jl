```
Element(nodes::Vector{Node}, nodeIndex::Vector{Int64}, section::Section, id::Symbol = nothing; release = :fixedfixed)
Element(nodeStart::Node, nodeEnd::Node, section::Section, id = :element; release = :fixedfixed)
```

Create a frame element with an optional `id` tag.

# Example

```julia-repl
julia> Element(nodes, [1,2], sec)
julia> Element(node1, node2, sec, :groundfloor_element)
```

# Optional argument `release`

This property enables decoupling of nodal DOFs with respect to the end of the element.

## Available releases:

  * :fixedfixed (default) - all DOFs are tied to nodes
  * :fixedfree - rotational DOFs are released at end node
  * :freefixed - rotational DOFs are released at start node
  * :freefree - all rotational DOFs are released (truss element)
  * :joist - all rotational DOFs except torsion are released

## Example

```julia-repl
julia> Element(nodes, [1,2], sec; release = :fixedfree)
```
