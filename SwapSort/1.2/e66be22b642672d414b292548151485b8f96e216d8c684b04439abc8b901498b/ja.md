```
tuplesort(t::Tuple; lt=isless, by=identity)
```

ソートされたタプルを返します。`lt` と `by` キーワードは `Base.sort` と同様に機能します。`tuplesort` は [`swapsort`](@ref) を呼び出し、最大64要素をサポートします。
