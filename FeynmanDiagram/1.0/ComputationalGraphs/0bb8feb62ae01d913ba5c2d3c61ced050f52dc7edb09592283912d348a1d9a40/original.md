```
function feynman_diagram(subgraphs::Vector{FeynmanGraph{F,W}}, topology::Vector{Vector{Int}}, perm_noleg::Union{Vector{Int},Nothing}=nothing;
    factor=one(_dtype.factor), weight=zero(_dtype.weight), name="", diagtype::DiagramType=GenericDiag()) where {F,W}
```

Create a FeynmanGraph representing feynman diagram from all subgraphs and topology (connections between vertices), where each ExternalVertex is given in `vertices`,  while internal vertices are constructed with external legs of graphs in `vertices`, or simply OperatorProduct in `vertices`.

# Arguments:

  * `subgraphs::Vector{FeynmanGraph{F,W}}` all subgraphs of the diagram. All external operators of subgraphs constitute all operators of the new diagram.
  * `topology::Vector{Vector{Int}}` topology of the diagram. Each Vector{Int} stores operators' index connected with each other (as a propagator).
  * `perm_noleg::Union{Vector{Int},Nothing}=nothing` permutation of all the nonleg external operators. By default, setting nothing means to use the default order from subgraphs.
  * `factor::F`  overall scalar multiplicative factor for this diagram (e.g., permutation sign)
  * `weight`  weight of the diagram
  * `name`  name of the diagram
  * `diagtype`  type of the diagram

# Example:

```julia-repl
julia> V = [𝑓⁺(1)𝑓⁻(2)𝜙(3), 𝑓⁺(4)𝑓⁻(5)𝜙(6), 𝑓⁺(7)𝑓⁻(8)𝜙(9)];
julia> g = feynman_diagram(interaction.(V), [[1, 5], [3, 9], [4, 8]], [3, 1, 2])
7:f⁺(1)f⁻(2)ϕ(3)|f⁺(4)f⁻(5)ϕ(6)|f⁺(7)f⁻(8)ϕ(9)=0.0=Ⓧ (1,2,3,4,5,6)

julia> g.subgraphs
6-element Vector{FeynmanGraph{Float64, Float64}}:
 1:f⁺(1)f⁻(2)ϕ(3)=0.0
 2:f⁺(4)f⁻(5)ϕ(6)=0.0
 3:f⁺(7)f⁻(8)ϕ(9)=0.0
 4:f⁺(1)|f⁻(5)⋅-1.0=0.0
 5:ϕ(3)|ϕ(9)=0.0
 6:f⁺(4)|f⁻(8)⋅-1.0=0.0
```
