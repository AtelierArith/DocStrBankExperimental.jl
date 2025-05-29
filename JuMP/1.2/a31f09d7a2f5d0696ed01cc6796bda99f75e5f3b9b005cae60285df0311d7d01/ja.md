```
@expressions(model, args...)
```

モデルに複数の式を一度に追加します。これは[`@expression`](@ref)マクロと同様の方法です。

モデルは最初の引数でなければならず、複数の式は`begin ... end`ブロック内で複数行にわたって追加できます。

このマクロは、定義された式を含むタプルを返します。

# 例

```julia
@expressions(model, begin
    my_expr, x^2 + y^2
    my_expr_1[i = 1:2], a[i] - z[i]
end)
```
