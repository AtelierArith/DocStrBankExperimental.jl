```
InternalConditions(functions=();
    dirichlet_nodes::Dict{Int,Int}=Dict{Int,Int}(),
    dudt_nodes::Dict{Int,Int}=Dict{Int,Int}(),
    parameters::Tuple=ntuple(_ -> nothing, length(functions)))
```

これは、PDEの内部条件を保持する[`InternalConditions`](@ref)構造体のコンストラクタです。さらに、[`Conditions`](@ref)（これを[`FVMProblem`](@ref)がラップしています）、[`ConditionType`](@ref)、および[`BoundaryConditions`](@ref)も参照してください。

# 引数

  * `functions::Union{<:Tuple,<:Function}=()`

内部条件を定義する関数です。これらは`edge_conditions`および`point_conditions`で参照される関数です。

# キーワード引数

  * `dirichlet_nodes::Dict{Int,Int}=Dict{Int,Int}()`

すべての[`Dirichlet`](@ref)点`u`をキーとして格納する`Dict`で、キーは`functions`および`parameters`内の対応する条件関数とパラメータを参照するインデックス`idx`にマッピングされます。

  * `dudt_nodes::Dict{Int,Int}=Dict{Int,Int}()`

すべての[`Dudt`](@ref)点`u`をキーとして格納する`Dict`で、キーは`functions`および`parameters`内の対応する条件関数とパラメータを参照するインデックス`idx`にマッピングされます。

  * `parameters::Tuple=ntuple(_ -> nothing, length(functions))`

関数のパラメータで、`parameters[i]`は`functions[i]`の引数`p`を提供します。

# 出力

返される値は対応する[`InternalConditions`](@ref)構造体です。

!!! note
    内部条件が境界条件と統合されるとき、境界に置かれた内部条件は、その境界上のポイントでの境界条件に置き換えられます。

