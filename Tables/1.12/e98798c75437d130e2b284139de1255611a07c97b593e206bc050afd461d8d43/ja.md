```
Tables.columnnames(::Union{AbstractColumns, AbstractRow}) => インデックス可能なコレクション
```

`AbstractColumns` または `AbstractRow` インターフェースオブジェクトの列名のリストを 1 ベースのインデックス可能なコレクション（`Tuple` や `Vector` のような）として取得します。デフォルトの定義は `propertynames(x)` を呼び出します。返される列名は一意でなければなりません。
