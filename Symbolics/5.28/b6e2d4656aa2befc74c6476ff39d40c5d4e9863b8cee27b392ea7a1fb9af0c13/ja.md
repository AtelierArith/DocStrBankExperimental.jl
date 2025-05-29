異なる微分を定義します。

# 例

```jldoctest
julia> using Symbolics

julia> @variables x y z;

julia> Dx = Differential(x); Dy = Differential(y);  # x と y に関する微分を作成

julia> Dx(z)  # z を x に関して微分
Differential(x)(z)

julia> Dy(z)  # z を y に関して微分
Differential(y)(z)
```
