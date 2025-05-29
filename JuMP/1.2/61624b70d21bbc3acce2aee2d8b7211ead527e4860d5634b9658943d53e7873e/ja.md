```
@NLconstraints(model, args...)
```

モデルに複数の非線形制約を一度に追加します。これは[`@NLconstraint`](@ref)マクロと同様の方法です。

モデルは最初の引数でなければならず、複数の制約は`begin ... end`ブロック内で複数行にわたって追加できます。

このマクロは、定義された制約を含むタプルを返します。

# 例

```julia
@NLconstraints(model, begin
    t >= sqrt(x^2 + y^2)
    [i = 1:2], z[i] <= log(a[i])
end)
```
