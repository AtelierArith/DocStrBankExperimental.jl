```
BagNode{T <: Union{AbstractMillNode, Missing}, B <: AbstractBags, C} <: AbstractBagNode
```

Data node that represents a multi-instance learning problem.

Contains instances stored in a subtree of type `T`, bag indices of type `B` and optional metadata of type `C`.

See also: [`WeightedBagNode`](@ref), [`AbstractBagNode`](@ref),     [`AbstractMillNode`](@ref), [`BagModel`](@ref).
