```
@NLexpressions(model, args...)
```

モデルに複数の非線形式を一度に追加します。これは[`@NLexpression`](@ref)マクロと同様の方法です。

モデルは最初の引数でなければならず、複数の式は`begin ... end`ブロック内で複数行にわたって追加できます。

このマクロは、定義された式を含むタプルを返します。

# 例

```julia
@NLexpressions(model, begin
    my_expr, sqrt(x^2 + y^2)
    my_expr_1[i = 1:2], log(a[i]) - z[i]
end)
```
