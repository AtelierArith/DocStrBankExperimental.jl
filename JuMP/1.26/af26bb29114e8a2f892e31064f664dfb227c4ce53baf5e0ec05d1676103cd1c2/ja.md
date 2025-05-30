```
PSDCone
```

正定半正定コーンオブジェクトで、[`@constraint`](@ref) マクロを使用して正定半正定な正方行列を制約するために使用できます。

行列が `Symmetric` 型の場合、その上三角部分の列ベクトル化（列を連結して得られるベクトル）は [`MOI.PositiveSemidefiniteConeTriangle`](@ref) セットに属するように制約されます。そうでない場合、その列ベクトル化は [`MOI.PositiveSemidefiniteConeSquare`](@ref) セットに属するように制約されます。

## 例

非対称の場合:

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> a = [x 2x; 2x x];

julia> b = [1 2; 2 4];

julia> cref = @constraint(model, a >= b, PSDCone())
[x - 1    2 x - 2
 2 x - 2  x - 4] ∈ PSDCone()

julia> jump_function(constraint_object(cref))
4-element Vector{AffExpr}:
 x - 1
 2 x - 2
 2 x - 2
 x - 4

julia> moi_set(constraint_object(cref))
MathOptInterface.PositiveSemidefiniteConeSquare(2)
```

対称の場合:

```jldoctest PSDCone
julia> using LinearAlgebra # For Symmetric

julia> model = Model();

julia> @variable(model, x);

julia> a = [x 2x; 2x x];

julia> b = [1 2; 2 4];

julia> cref = @constraint(model, Symmetric(a - b) in PSDCone())
[x - 1  2 x - 2
 ⋯      x - 4] ∈ PSDCone()

julia> jump_function(constraint_object(cref))
3-element Vector{AffExpr}:
 x - 1
 2 x - 2
 x - 4

julia> moi_set(constraint_object(cref))
MathOptInterface.PositiveSemidefiniteConeTriangle(2)
```
