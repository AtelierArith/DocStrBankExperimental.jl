```
GroupActions(actions::Function...)
```

一連の群作用 `(f1, f2, f3, ...)` を保存します。各作用はタプルを返す必要があります。作用は次のように適用されます。

1. f1 が元の解 `s` に適用されます
2. f2 が `s` と 1 の結果に適用されます
3. f3 が `s` と 1) および 2) の結果に適用されます

このように続きます。

## 例

```julia-repl
julia> f1(s) = (s * s,);

julia> f2(s) = (2s, -s, 5s);

julia> f3(s) = (s + 1,);

julia> GroupActions(f1)(3)
(3, 9)

julia> GroupActions(f1, f2)(3)
(3, 9, 6, -3, 15, 18, -9, 45)

julia> GroupActions(f1,f2, f3)(3)
(3, 9, 6, -3, 15, 18, -9, 45, 4, 10, 7, -2, 16, 19, -8, 46)
```
