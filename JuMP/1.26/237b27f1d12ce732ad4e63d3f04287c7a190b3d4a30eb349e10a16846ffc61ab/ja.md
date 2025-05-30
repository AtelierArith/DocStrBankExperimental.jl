```
set_nonlinear_dual_start_value(
    model::Model,
    start::Union{Nothing,Vector{Float64}},
)
```

MOI属性[`MOI.NLPBlockDualStart`](@ref)の値を設定します。

!!! compat
    この関数はレガシー非線形インターフェースの一部です。 [非線形モデリング](@ref)で文書化されている新しい非線形インターフェースの使用を検討してください。


スタートベクトルは、[`all_nonlinear_constraints`](@ref)によって与えられた順序で非線形制約のラグランジュ双対に対応します。つまり、単一の関数呼び出しで非線形制約すべてに対応する単一のスタートベクトルを渡す必要があります。非線形制約の双対スタート値を1つずつ設定することはできません。以下の例では、[`all_nonlinear_constraints`](@ref)を使用して非線形制約の参照とスタートベクトルとのマッピングを作成する方法を示しています。

以前のスタートを解除するには`nothing`を渡します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2]);

julia> nl1 = @NLconstraint(model, x[1] <= sqrt(x[2]));

julia> nl2 = @NLconstraint(model, x[1] >= exp(x[2]));

julia> start = Dict(nl1 => -1.0, nl2 => 1.0);

julia> start_vector = [start[con] for con in all_nonlinear_constraints(model)]
2-element Vector{Float64}:
 -1.0
  1.0

julia> set_nonlinear_dual_start_value(model, start_vector)

julia> nonlinear_dual_start_value(model)
2-element Vector{Float64}:
 -1.0
  1.0
```
