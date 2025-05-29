```
NodeData
```

A `DataType` for storing values in an expression tree that is used in a  [`NLPExpr`](@ref). Acceptable value types include:

  * `Real`: Constants
  * `GeneralVariableRef`: Optimization variables
  * `JuMP.GenericAffExpr{Float64, GeneralVariableRef}`: Affine expressions
  * `JuMP.GenericQuadExpr{Float64, GeneralVariableRef}`: Quadratic expressions
  * `Symbol`: Registered NLP function name.

**Fields**

  * `value`: The stored value.
