```
flatten(obj, use=Real)
```

階層型を `use` 型の要素を持つタプルにフラット化します。

# 例

```jldoctest
julia> flatten((a=(Complex(1, 2), 3), b=4))
(1, 2, 3, 4)

```

タプルをベクターに変換するには、単に [flatten(x)...] を使用するか、静的配列を使用してアロケーションを避ける: `SVector(flatten(x))` を使用します。
