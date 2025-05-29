```
PredictiveSearch(dat::DoubleArrayTrie, key::AbstractString)
```

接頭辞 `prefix` を持つトライ内のすべての文字列を反復する iterable オブジェクトを返します。各要素は id と文字列のタプル (`Tuple{Int, String}`) になります。
