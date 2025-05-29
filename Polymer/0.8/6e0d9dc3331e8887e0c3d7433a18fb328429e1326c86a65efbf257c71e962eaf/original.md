```
ObjType{name}
```

A type representing the type of an object defined in Polymer.jl.

A `ObjType` object can be passed to the first argument of [`make`](@ref) to dispatch to the correction version of this method to create an object designated by `name`:

  * :System: PolymerSystem
  * :Component: Component
  * :χN_map: Dict{Set{Symbol},AbstractFloat}
  * :Specie: AbstractSpecie (KuhnSegment) and SmallMolecule
  * :SMOL: SmallMolecule
  * :BCP: BlockCopolymer
  * :Block: PolymerBlock
  * :BlockEnd: BlockEnd (FreeEnd and BranchPoint)
