```
Tables.schema(x) => Union{Nothing, Tables.Schema}
```

`Tables.rows` または `Tables.columns` によって返されたオブジェクトのスキーマを取得しようとします。`AbstractRow` イテレータまたは `AbstractColumns` オブジェクトがそのスキーマを決定できない場合、`nothing` が返されます。それ以外の場合、列名と型が利用可能な `Tables.Schema` オブジェクトが返されます。
