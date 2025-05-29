```
AbstractExpressionNode{T} <: AbstractNode
```

Abstract type for nodes that represent an expression. Along with the fields required for `AbstractNode`, this additionally must have fields for:

  * `constant::Bool`: Whether the node is a constant.
  * `val::T`: Value of the node. If `degree==0`, and `constant==true`,   this is the value of the constant. It has a type specified by the   overall type of the `Node` (e.g., `Float64`).
  * `feature::UInt16`: Index of the feature to use in the   case of a feature node. Only used if `degree==0` and `constant==false`.    Only defined if `degree == 0 && constant == false`.
  * `op::UInt8`: If `degree==1`, this is the index of the operator   in `operators.unaops`. If `degree==2`, this is the index of the   operator in `operators.binops`. In other words, this is an enum   of the operators, and is dependent on the specific `OperatorEnum`   object. Only defined if `degree >= 1`

# Interface

See [`NodeInterface`](@ref DynamicExpressions.InterfacesModule.NodeInterface) for a full description of the interface implementation, as well as tests to verify correctness.

You *must* define `CustomNode{_T} where {_T} = new{_T}()` for each custom node type, as well as `constructorof` and `with_type_parameters`.

In addition, you *may* choose to define the following functions, to override the defaults behavior, in particular if you wish to add additional fields to your type.

  * `leaf_copy` and `branch_copy`
  * `leaf_convert` and `branch_convert`
  * `leaf_equal` and `branch_equal`
  * `leaf_hash` and `branch_hash`
  * `preserve_sharing`
