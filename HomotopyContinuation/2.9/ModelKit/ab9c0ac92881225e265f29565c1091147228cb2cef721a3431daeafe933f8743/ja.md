```
to_dict(expr::Expression, vars::AbstractVector{Variable})
```

与えられた変数 `vars` に関して `expr` の係数を返します。`expr` が展開されており、多項式を表していると仮定します。有理式が遭遇した場合は `PolynomialError` をスローします。
