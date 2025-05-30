```
@NLexpressions(model, args...)
```

モデルに複数の非線形式を一度に追加します。これは[`@NLexpression`](@ref)マクロと同様の方法です。

モデルは最初の引数でなければならず、複数の式は`begin ... end`ブロック内で複数行にわたって追加できます。

このマクロは、定義された式を含むタプルを返します。

!!! compat
    このマクロはレガシー非線形インターフェースの一部です。[非線形モデリング](@ref)で文書化された新しい非線形インターフェースの使用を検討してください。ほとんどの場合、`@NLexpressions`を[`@expressions`](@ref)に置き換えることができます。


## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> @variable(model, y);

julia> @variable(model, z[1:2]);

julia> a = [4, 5];

julia> @NLexpressions(model, begin
           my_expr, sqrt(x^2 + y^2)
           my_expr_1[i = 1:2], log(a[i]) - z[i]
       end)
(subexpression[1]: sqrt(x ^ 2.0 + y ^ 2.0), NonlinearExpression[subexpression[2]: log(4.0) - z[1], subexpression[3]: log(5.0) - z[2]])
```
