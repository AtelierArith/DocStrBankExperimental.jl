```
implied_literals(root::LogicCircuit)::Union{BitSet, Nothing}
```

Compute at each node literals that are implied by the formula.  `nothing` at a node means all literals are implied (i.e. the node's formula is false)

This algorithm is sound but not complete - all literals returned are correct, but some true implied literals may be missing. 
