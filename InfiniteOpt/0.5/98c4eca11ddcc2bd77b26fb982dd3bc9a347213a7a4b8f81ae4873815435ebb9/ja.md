```
JuMP.delete(model::InfiniteModel, fref::ParameterFunctionRef)::Nothing
```

`JuMP.delete`を拡張して、パラメータ関数とその依存関係を削除します。`fref`が無効な場合、すなわち既に削除されているか、別のモデルに属している場合はエラーを返します。
