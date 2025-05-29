```
coefficients(f::Expression, vars::AbstractVector{Variable}; expanded = false)
```

与えられた変数 `vars` に対する与えられた多項式 `f` のすべての係数を返します。`expanded = true` の場合、これは式 `f` がすでに展開されていると仮定します。たとえば、[`expand`](@ref) を使用して。
