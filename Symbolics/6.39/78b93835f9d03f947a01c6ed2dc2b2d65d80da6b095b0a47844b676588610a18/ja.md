```julia
symbolic_linear_solve(eq, var; simplify, check) -> Any

```

方程式 `eqs` を変数のセット `vars` に対して解きます。

`length(eqs) == length(vars)` であることを前提としています。

現在のところ、すべての方程式が線形である場合にのみ機能します。`check` は expr が `vars` に関して線形であるかどうかを確認します。

# 例

```jldoctest
julia> @variables x y
2-element Vector{Num}:
 x
 y

julia> Symbolics.symbolic_linear_solve(x + y ~ 0, x)
-y

julia> Symbolics.symbolic_linear_solve([x + y ~ 0, x - y ~ 2], [x, y])
2-element Vector{Float64}:
  1.0
 -1.0
```
