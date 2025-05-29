```julia
struct ConstraintViolation{S<:ValueConstraints.Interface.AbstractConstraint} <: Exception
```

  * `constraint::ValueConstraints.Interface.AbstractConstraint`: 違反された `constraint`。
  * `value::Any`: 制約に違反した `value`。

`constraint` に対して検証に失敗した `value` を表す `Exception`。

特定の [`AbstractConstraint`](@ref) に対して `ConstraintViolation` が生成されるときに説明的なエラーメッセージを表示するには、対応する `Base.print(io::IO, violation::ConstraintViolation{AbstractConstraint})` メソッドを定義します。

[`CompoundConstraint`](@ref) のエラーを説明するには特別な注意が必要です。詳細については [`Base.print(io::IO, violation::ConstraintViolation{<:CompoundConstraint})`](@ref) を参照してください。
