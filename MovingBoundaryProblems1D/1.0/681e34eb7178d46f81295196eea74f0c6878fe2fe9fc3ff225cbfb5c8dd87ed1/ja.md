```
BoundaryConditions{L<:Union{<:Dirichlet, <:Neumann},R<:Union{<:Dirichlet, <:Neumann},M<:Robin}
```

`MBProblem`の境界条件。

# フィールド

  * `lhs::L`: 左側の境界条件。`Dirichlet`または`Neumann`でなければなりません。
  * `rhs::R`: 右側の境界条件。`Dirichlet`または`Neumann`でなければなりません。
  * `moving_boundary::M`: 移動境界条件。`Robin`でなければなりません。

構築できる境界条件のタイプについては、[`Dirichlet`](@ref)、[`Neumann`](@ref)、および[`Robin`](@ref)も参照してください。
