```
ConstantTerm{T<:Number} <: AbstractTerm
```

数式におけるリテラル数を表します。デフォルトでは、[`apply_schema`](@ref)によって[`InterceptTerm`]に変換されます。

# フィールド

  * `n::T`: この項によって表される数。
