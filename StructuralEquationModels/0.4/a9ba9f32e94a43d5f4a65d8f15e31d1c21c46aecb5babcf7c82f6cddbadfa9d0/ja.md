```
sort_vars(partable::ParameterTable)
sort_vars(partables::EnsembleParameterTable)
```

`partable`内の変数をソートし、すべての独立変数が従属変数の前に来るようにし、ソートされた変数が`partable.sorted_vars`にある`partable`のコピーを返します。

インプレースバージョンについては、[sort_vars!](@ref)を参照してください。
