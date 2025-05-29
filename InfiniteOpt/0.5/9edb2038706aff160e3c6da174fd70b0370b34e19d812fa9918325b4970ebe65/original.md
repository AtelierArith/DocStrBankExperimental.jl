```
NLPExpr <: JuMP.AbstractJuMPScalar
```

A `DataType` for storing scalar nonlinear expressions. It stores the expression  algebraically via an expression tree where each node contains [`NodeData`](@ref)  that can store one of the following:

  * a registered function name (stored as a `Symbol`)
  * a constant
  * a variable
  * an affine expression
  * a quadratic expression.

Specifically, it employs a left-child right-sibling tree  (from `LeftChildRightSiblingTrees.jl`) to represent the expression tree.

**Fields**

  * `tree_root::LeftChildRightSiblingTrees.Node{NodeData}`: The root node of the  expression tree.
