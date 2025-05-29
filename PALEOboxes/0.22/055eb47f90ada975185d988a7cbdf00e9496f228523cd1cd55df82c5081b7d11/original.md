```
AbstractVarList
```

Variables required by a [`ReactionMethod`](@ref) `methodfn` are specified by  a Tuple of VarList_xxx <: AbstractVarList, each containing a collection of [`VariableReaction`](@ref).

These are then converted (by the [`create_accessors`](@ref) method) to a corresponding Tuple of collections of views on Domain data arrays , which are then be passed to the [`ReactionMethod`](@ref) `methodfn`.

NB: creates and uses a copy of supplied Variables including metadata, so set / modify Variable attributes *before* creating a VarList.

# Implementation

Subtypes of `AbstractVarList` should implement:

  * a constructor that takes a collection of VariableReactions
  * [`create_accessors`](@ref), returning the views on Domain data arrays in a subtype-specific collection.
  * [`get_variables`](@ref), returning the collection of VariableReactions (as a flat list).
