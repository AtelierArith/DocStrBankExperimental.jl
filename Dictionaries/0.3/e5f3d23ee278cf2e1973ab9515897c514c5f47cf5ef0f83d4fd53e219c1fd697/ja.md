```
insert!(dict::AbstractDictionary, i, value)
```

`value`を新しいインデックス`i`に`dict`に挿入します。インデックス`i`がすでに存在する場合はエラーが発生します。

ヒント: 既存の値を更新するには`setindex!`を使用し、"upsert"（更新または挿入）操作を行うには`set!`を使用します。
