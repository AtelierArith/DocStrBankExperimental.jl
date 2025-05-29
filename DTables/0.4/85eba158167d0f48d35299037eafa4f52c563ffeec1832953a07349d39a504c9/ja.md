```
DTable(loader_function, files::Vector{String}; tabletype=nothing)
```

ファイル名のリストと `loader_function` を使用して `DTable` を構築します。パーティショニングは提供されたファイルの内容に基づいており、つまり1つのファイルが1つのパーティションを作成するために使用されます。

`tabletype` キーワード引数を提供すると、内部のテーブルパーティションタイプが上書きされます。
