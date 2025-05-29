```
@constraints(model, args...)
```

一度に制約のグループを追加します。これは[`@constraint`](@ref)マクロと同様の方法です。

モデルは最初の引数でなければならず、複数の制約を`begin ... end`ブロック内で複数行にわたって追加できます。

このマクロは、定義された制約を含むタプルを返します。

# 例

```julia
@constraints(model, begin
    x >= 1
    y - w <= 2
    sum_to_one[i=1:3], z[i] + y == 1
end)
```
