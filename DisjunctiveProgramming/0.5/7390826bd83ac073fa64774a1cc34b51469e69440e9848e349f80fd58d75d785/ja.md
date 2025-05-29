```
Disjunction{M <: JuMP.AbstractModel} <: AbstractConstraint
```

一意の [`LogicalVariableIndex`](@ref) によって示される不等式のコレクションで構成される不等式制約の型です。

**フィールド**

  * `indicators::Vector{LogicalVariableref}`: 各不等式を一意に識別する論理変数への参照

(indicators)。

  * `nested::Bool`: この不等式は別の不等式の中にネストされていますか？
