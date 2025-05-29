```
reorder(X::AbstractArray, orders)
```

`X`を`orders`に従って再配置します。

!!! tip
    `orders`は任意の反復可能なもので構いませんが、パフォーマンスを最大限に引き出すために`Tuple`が推奨されます。しかし、変換にそれほど時間はかかりません。

