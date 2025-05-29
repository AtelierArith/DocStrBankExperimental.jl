```
PSDCone
```

正定半正コーンオブジェクトで、[`@constraint`](@ref)マクロで正定半正の平方行列を制約するために使用できます。行列が`Symmetric`型の場合、その上三角部分の列ベクトル化（列を連結して得られるベクトル）は`MOI.PositiveSemidefiniteConeTriangle`集合に属するように制約されます。そうでない場合、その列ベクトル化は`MOI.PositiveSemidefiniteConeSquare`集合に属するように制約されます。

## 例

次の例を考えてみましょう：

```jldoctest PSDCone; setup = :(using JuMP)
julia> model = Model();

julia> @variable(model, x)
x

julia> a = [ x 2x
            2x  x];

julia> b = [1 2
            2 4];

julia> cref = @constraint(model, a >= b, PSDCone())
[x - 1    2 x - 2;
 2 x - 2  x - 4  ] ∈ PSDCone()

julia> jump_function(constraint_object(cref))
4-element Array{GenericAffExpr{Float64,VariableRef},1}:
 x - 1
 2 x - 2
 2 x - 2
 x - 4

julia> moi_set(constraint_object(cref))
MathOptInterface.PositiveSemidefiniteConeSquare(2)
```

最後のコマンドの出力から、行列のベクトル化が`PositiveSemidefiniteConeSquare`に属するように制約されていることがわかります。

```jldoctest PSDCone
julia> using LinearAlgebra # For Symmetric

julia> cref = @constraint(model, Symmetric(a - b) in PSDCone())
[x - 1    2 x - 2;
 2 x - 2  x - 4  ] ∈ PSDCone()

julia> jump_function(constraint_object(cref))
3-element Array{GenericAffExpr{Float64,VariableRef},1}:
 x - 1
 2 x - 2
 x - 4

julia> moi_set(constraint_object(cref))
MathOptInterface.PositiveSemidefiniteConeTriangle(2)
```

最後のコマンドの出力から、行列の上三角部分のみのベクトル化が`PositiveSemidefiniteConeSquare`に属するように制約されていることがわかります。
