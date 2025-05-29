```
Identifier(dataset::DataSet, collection::Union{Symbol, Nothing}=:name,
           name::Symbol=something(collection, :name))
```

`dataset`を参照する`Identifier`を作成し、`collection`が`nothing`でない場合は、`dataset`がどのコレクションから来ているかを指定し、すべてのパラメータを指定しますが、型情報は含めません。

`collection`と`name`は、シンボル`:name`にデフォルト設定され、生成された`Identifier`のコレクションとデータセットの参照がコレクション/データセットの*名前*を使用することを示します。`:uuid`に設定された場合は、代わりにUUIDが使用されます。他の値のシンボルはサポートされていません。
