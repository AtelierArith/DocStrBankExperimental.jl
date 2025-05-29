異なる微分を1つ以上定義します。

# 例

```jldoctest
julia> using Symbolics

julia> @variables x y z;

julia> Dx = Differential(x); Dy = Differential(y);  # xおよびyに関する微分を作成

julia> Dx(z)  # zをxに関して微分
Differential(x)(z)

julia> Dy(z)  # zをyに関して微分
Differential(y)(z)
```
