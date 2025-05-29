```
もし(modify_condition)
```

`modify_condition` が成り立つ場所へのアクセスを制限します。

```jldoctest
julia> using Accessors

julia> obj = (1,2,3,4,5,6);

julia> @set obj |> Elements() |> If(iseven) *= 10
(1, 20, 3, 40, 5, 60)
```

この関数/型は実験的です。警告なしにいつでも変更または削除される可能性があります。
