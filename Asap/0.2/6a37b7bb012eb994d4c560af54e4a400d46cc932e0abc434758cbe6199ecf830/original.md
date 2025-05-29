```
TrussElement(nodes::Vector{TrussNode}, nodeIndex::Vector{Int64}, section::AbstractSection, id = :element)
TrussElement(nodeStart::TrussNode, nodeEnd::TrussNode, section::AbstractSection, id = :element)
```

Create a truss element.

# Example

```julia-repl
julia> TrussElement(nt, [1,2], sec)
TrussElement(Section(794.0, 200000.0, 77000.0, 737000.0, 737000.0, 1.47e6, 1.0), [1, 2], TrussNode([0.8879630592102802, 0.6713937498337156, 0.617463764682365], Bool[0, 0, 0], #undef, [0.0, 0.0, 0.0], [0.0, 0.0, 0.0], nothing), TrussNode([0.16046742214916832, 0.15869760269854827, 0.6247762072043447], Bool[1, 1, 1], #undef, [0.0, 0.0, 0.0], [0.0, 0.0, 0.0], nothing), #undef, 0.8900341077991537, #undef, #undef, #undef, 1.5707963267948966, #undef, nothing)
```
