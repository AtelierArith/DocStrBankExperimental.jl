```
mutable struct Graph{F<:Number,W}
```

A representation of a computational graph, e.g., an expression tree, with type stable node data.

# Members:

  * `id::Int`  the unique hash id to identify the diagram
  * `name::Symbol`  name of the diagram
  * `orders::Vector{Int}`  orders associated with the graph, e.g., derivative orders
  * `subgraphs::Vector{Graph{F,W}}`  vector of sub-diagrams
  * `subgraph_factors::Vector{F}`  scalar multiplicative factors associated with each subgraph. Note that the subgraph factors may be manipulated algebraically. To associate a fixed multiplicative factor with this graph which carries some semantic meaning, use the `factor` argument instead.
  * `operator::DataType`  node operation. Addition and multiplication are natively supported via operators Sum and Prod, respectively. Should be a concrete subtype of `AbstractOperator`.
  * `weight::W`  the weight of this node
  * `properties::Any` extra information of Green's functions.

# Example:

```julia-repl
julia> g1 = Graph([])
1=0.0

julia> g2 = Graph([]; factor=2)
2⋅2.0=0.0

julia> g = Graph([g1, g2]; operator=ComputationalGraphs.Sum())
3=0.0=⨁ (1,2)
```
