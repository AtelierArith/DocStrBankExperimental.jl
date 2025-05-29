```
get(var::ContextVar{T}) -> Union{Some{T},Nothing}
```

`Some(value)`を返します。`value`が`var`に割り当てられている場合。未割り当ての場合は`nothing`を返します。
