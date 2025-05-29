```
is_no_constprop(method::Union{Method,CodeInfo}) -> Bool
```

`method`が`Base.@constprop :none`として宣言されているかどうかを確認します。
