```julia
struct Difference <: Symbolics.Operator
```

差分演算子を表します。

# フィールド

  * `t`: 固定差分
  * `dt`
  * `update`

# 例

```jldoctest
julia> using Symbolics

julia> @variables t;

julia> Δ = Difference(t; dt=0.01)
(::Difference) (generic function with 2 methods)
```
