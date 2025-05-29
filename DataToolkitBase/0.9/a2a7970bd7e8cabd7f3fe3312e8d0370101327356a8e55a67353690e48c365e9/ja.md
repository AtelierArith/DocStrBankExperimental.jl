```
resolve(collection::DataCollection, ident::Identifier;
        resolvetype::Bool=true, requirematch::Bool=true)
```

識別子（`ident`）を特定のデータセットに解決しようとします。マッチするデータセットは `collection` から検索されます。

`resolvetype` が設定され、`ident` がデータ型を指定する場合、特定されたデータセットはその型に読み込まれます。

`requirematch` が設定されている場合、`ident` にマッチするデータセットがないとエラーが発生します。そうでない場合は、`nothing` が返されます。
