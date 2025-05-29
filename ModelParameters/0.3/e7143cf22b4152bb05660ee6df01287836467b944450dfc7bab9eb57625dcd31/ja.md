```
withunits(object, [fieldname])
withunits(model::AbstractModel, [fieldname])
withunits(param::AbstractParam, [fieldname])
```

指定された `fieldname`（デフォルトは `:val`）によって、単一の `Param` のフィールドを返すか、`Model` または任意のオブジェクト内の `Param` のタプルを返します。

`units` フィールドがある場合、返される値は指定されたフィールドと `units` フィールドの組み合わせになります。

`units` フィールドがない場合や特定の `Param` の `units` フィールドが `nothing` を含む場合、フィールド値は変更されずに返されます。
