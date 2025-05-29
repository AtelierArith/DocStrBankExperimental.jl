```
SortedDict(iter, o=Forward)
```

および `SortedDict{K,V}(iter, o=Forward)`

任意の反復可能なオブジェクトから `key=>value` ペアの `SortedDict` を構築します。`K` と `V` が指定されていない場合、キーの型と値の型は与えられた反復可能なオブジェクトから推測されます。順序オブジェクト `o` のデフォルトは `Forward` です。
