```
horner(f::Expression, vars = variables(f))
```

多変数ホーナー法則を使用して `f` を再構成します。

### 例

```julia-repl
julia> @var u v c[1:3]
(u, v, Variable[c₁, c₂, c₃])

julia> f = c[1] + c[2] * v + c[3] * u^2 * v^2 + c[3]u^3 * v
c₁ + v*c₂ + u^2*v^2*c₃ + u^3*v*c₃

julia> horner(f)
c₁ + v*(c₂ + u^3*c₃ + u^2*v*c₃)
```
