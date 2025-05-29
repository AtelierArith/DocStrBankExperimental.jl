```
function JuMP.build_constraint(
    _error::Function, 
    func::AbstractVector{T},
    set::S
) where {T <: Union{LogicalVariableRef, _LogicalExpr}, S <: Union{Exactly, AtLeast, AtMost}}
```

`JuMP.build_constraint`を拡張して、[`GDPModel`](@ref)に論理的なカーディナリティ制約を追加します。これにより、`JuMP.add_constraint`と組み合わせて、`@constraint(model, [name], logical_expr in set)`を使用できるようになります。ここで、setは次のいずれかのカーディナリティセットであることができます：`AtLeast(n)`、`AtMost(n)`、または`Exactly(n)`。

## 例

論理変数`Y`を正確に1つ`true`に選択するには、次のようにします（`AtLeast(n)`や`AtMost(n)`でも同様のことができます）：

```julia
using DisjunctiveProgramming
model = GDPModel();
@variable(model, Y[i = 1:2], LogicalVariable);
@constraint(model, [Y[1], Y[2]] in Exactly(1));
```
