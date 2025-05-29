```julia
struct Shift <: Symbolics.Operator
```

シフト演算子を表します。

# フィールド

  * `t`: 固定シフト
  * `steps`

# 例

```jldoctest
julia> using Symbolics

julia> @variables t;

julia> Δ = Shift(t)
(::Shift) (generic function with 2 methods)
```
