```julia
struct Differential <: Symbolics.Operator
```

微分演算子を表します。

# フィールド

  * `x`: 微分する変数または式。

# 例

```jldoctest
julia> using Symbolics

julia> @variables x y;

julia> D = Differential(x)
(D'~x)

julia> D(y) # yをxに関して微分
(D'~x)(y)

julia> Dx = Differential(x) * Differential(y) # d^2/dxy 演算子
(D'~x(t)) ∘ (D'~y(t))

julia> D3 = Differential(x)^3 # 3次微分演算子
(D'~x(t)) ∘ (D'~x(t)) ∘ (D'~x(t))
```
