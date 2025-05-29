```
name_only(f::FuncArg; is_splat::Bool=f.is_splat) -> FuncArg
```

`f`から型を削除した新しい`FuncArg`を返します。

`f.name`が提供されている場合、`f`から値フィールドも削除します。
