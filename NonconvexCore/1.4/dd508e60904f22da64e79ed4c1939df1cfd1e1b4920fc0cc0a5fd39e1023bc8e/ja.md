```
struct Model <: AbstractModel
    objective::Objective
    eq_constraints::VectorOfFunctions
    ineq_constraints::VectorOfFunctions
    box_min::AbstractVector
    box_max::AbstractVector
    init::AbstractVector
    integer::AbstractVector
end
```

`Model`構造体は非線形最適化問題に関する情報を格納します。

  * `objective`: 問題の目的関数で、型は[`Objective`](@ref)です。
  * `eq_constraints`: 問題の等式制約で、型は[`VectorOfFunctions`](@ref)です。`ineq_constraints`内の各関数は[`IneqConstraint`](@ref)または[`AbstractFunction`](@ref)のインスタンスである可能性があります。関数が`IneqConstraint`でない場合、その右辺の制約は0であると仮定されます。
  * `ineq_constraints`: 問題の不等式制約で、型は[`VectorOfFunctions`](@ref)です。`ineq_constraints`内の各関数は[`IneqConstraint`](@ref)または[`AbstractFunction`](@ref)のインスタンスである可能性があります。関数が`IneqConstraint`でない場合、その右辺の制約は0であると仮定されます。
  * `sd_constraints`: 任意の実行可能な解において正半定値でなければならない行列値関数のリストです。
