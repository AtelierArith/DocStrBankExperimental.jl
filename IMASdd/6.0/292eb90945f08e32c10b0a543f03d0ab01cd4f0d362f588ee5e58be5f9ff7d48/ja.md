```
hasexpr(@nospecialize(ids::IDS), field::Symbol)
```

idsフィールドが式を持っている場合はtrueを返します。

式を持っていることは、それが式であることを意味しません。そのためには、`isexpr(ids, field)`を使用してください。

注意: 式を評価しません。
