```
CommonPrefixSearch(dat::DoubleArrayTrie, key::AbstractString)
```

`key`と共通の接頭辞を持つトライ内のすべての文字列を反復するイテラブルオブジェクトを返します。各要素はidと文字列のタプル（`Tuple{Int, String}`）です。
