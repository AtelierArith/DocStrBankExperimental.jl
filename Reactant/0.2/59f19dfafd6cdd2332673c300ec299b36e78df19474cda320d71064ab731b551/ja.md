```
DotGeneralAlgorithm(
    ::Type{lhsT}, ::Type{rhsT}, ::Type{accumT},
    rhs_component_count::Int, lhs_component_count::Int, num_primitive_operations::Int,
    allow_imprecise_accumulation::Bool
)
DotGeneralAlgorithm{lhsT,rhsT,accumT}(
    lhs_component_count::Int, rhs_component_count::Int, num_primitive_operations::Int,
    allow_imprecise_accumulation::Bool
)
```

`stablehlo.dot_general` 操作の構成を表します。

# 引数

  * `lhsT`: 左辺オペランドの型。
  * `rhsT`: 右辺オペランドの型。
  * `accumT`: 加算オペランドの型。
  * `lhs_component_count`: 左辺オペランドのコンポーネントの数。
  * `rhs_component_count`: 右辺オペランドのコンポーネントの数。
  * `num_primitive_operations`: `stablehlo.dot_general` 操作の原始操作の数。
