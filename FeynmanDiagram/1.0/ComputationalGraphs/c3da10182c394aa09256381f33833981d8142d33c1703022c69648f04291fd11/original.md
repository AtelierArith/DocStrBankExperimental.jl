```
mutable struct FeynmanGraph{F<:Number,W}

Computational graph representation of a (collection of) Feynman diagram(s). All Feynman diagrams should share the same set of external and internal vertices.
```

# Members:

  * `id::Int`  the unique hash id to identify the diagram
  * `name::Symbol`  name of the diagram
  * `orders::Vector{Int}`  orders associated with the Feynman graph, e.g., loop/derivative orders
  * `properties::FeynmanProperties`  diagrammatic properties, e.g., the operator vertices and topology
  * `subgraphs::Vector{FeynmanGraph{F,W}}`  vector of sub-diagrams
  * `subgraph_factors::Vector{F}`  scalar multiplicative factors associated with each subdiagram
  * `operator::DataType`  node operation (Sum, Prod, etc.)
  * `weight::W`  weight of the diagram

# Example:

```julia-repl
julia> g1 = FeynmanGraph([]; vertices=[𝑓⁺(1),𝑓⁻(2)], external_indices=[1,2], external_legs=[true,true])
1:f⁺(1)|f⁻(2)=0.0

julia> g2 = FeynmanGraph([]; vertices=[𝑓⁺(3),𝑓⁻(4)], external_indices=[1,2], external_legs=[true,true])
2:f⁺(3)|f⁻(4)=0.0

julia> g = FeynmanGraph([g1,g2]; vertices=[𝑓⁺(1),𝑓⁻(2),𝑓⁺(3),𝑓⁻(4)], operator=ComputationalGraphs.Prod(), external_indices=[1,2,3,4], external_legs=[true,true,true,true])
3:f⁺(1)|f⁻(2)|f⁺(3)|f⁻(4)=0.0=Ⓧ (1,2)
```
