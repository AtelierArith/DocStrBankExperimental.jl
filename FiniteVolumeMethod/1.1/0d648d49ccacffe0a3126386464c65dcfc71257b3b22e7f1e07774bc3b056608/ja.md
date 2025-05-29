```
Conditions{F} <: AbstractConditions
```

これはPDEの境界条件と内部条件を保持する`struct`です。コンストラクタは次のとおりです。

```
Conditions(mesh::FVMGeometry, bc::BoundaryConditions, ic::InternalConditions=InternalConditions())
```

フィールドは次のとおりです：

# フィールド

  * `neumann_conditions::Dict{NTuple{2,Int},Int}`

すべての[`Neumann`](@ref)エッジ`(u, v)`をキーとして格納する`Dict`で、キーは対応する条件関数と`functions`内のパラメータを参照するインデックス`idx`にマッピングされます。

  * `constrained_conditions::Dict{NTuple{2,Int},Int}`

すべての[`Constrained`](@ref)エッジ`(u, v)`をキーとして格納する`Dict`で、キーは対応する条件関数と`functions`内のパラメータを参照するインデックス`idx`にマッピングされます。

  * `dirichlet_conditions::Dict{Int,Int}`

すべての[`Dirichlet`](@ref)ポイント`u`をキーとして格納する`Dict`で、キーは対応する条件関数と`functions`内のパラメータを参照するインデックス`idx`にマッピングされます。

  * `dudt_conditions::Dict{Int,Int}`

すべての[`Dudt`](@ref)ポイント`u`をキーとして格納する`Dict`で、キーは対応する条件関数と`functions`内のパラメータを参照するインデックス`idx`にマッピングされます。

  * `functions::F<:Tuple`

境界条件と内部条件を定義する関数です。`i`番目の関数は、DelaunayTriangulation.jlで定義された`i`番目の境界インデックスに対応する`mesh`の境界部分に対応する必要があります。`i`番目の関数は[`ParametrisedFunction`](@ref)として格納されます。
