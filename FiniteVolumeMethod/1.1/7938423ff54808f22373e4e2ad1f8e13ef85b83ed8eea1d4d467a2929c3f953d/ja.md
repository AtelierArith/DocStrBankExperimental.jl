```
BoundaryConditions(mesh::FVMGeometry, functions, conditions; parameters=nothing)
```

これは、PDEの境界条件を保持する[`BoundaryConditions`](@ref)構造体のコンストラクタです。 [`Conditions`](@ref)（[`FVMProblem`](@ref)がこれをラップするもの）、[`ConditionType`](@ref)、および[`InternalConditions`](@ref)も参照してください。

# 引数

  * `mesh::FVMGeometry`

PDEが定義されているメッシュ。

  * `functions::Union{<:Tuple,<:Function}`

境界条件を定義する関数。`i`番目の関数は、DelaunayTriangulation.jlで定義された`i`番目の境界インデックスに対応するメッシュの境界部分に対応する必要があります。

  * `conditions::Union{<:Tuple,<:ConditionType}`

上記の各境界インデックスに対応する境界条件タイプの分類。可能な条件については[`ConditionType`](@ref)を参照してください - [`Neumann`](@ref)、[`Dudt`](@ref)、[`Dirichlet`](@ref)、または[`Constrained`](@ref)のいずれかである必要があります。

# キーワード引数

  * `parameters=ntuple(_ -> nothing, length(functions))`

関数のパラメータで、`parameters[i]`は`functions[i]`の引数`p`を提供します。

# 出力

返される値は、対応する[`BoundaryConditions`](@ref)構造体です。
