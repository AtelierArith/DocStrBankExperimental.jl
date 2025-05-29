```
swapsort(a...; lt=isless, by=identity)
```

引数をソートし、ソートされたタプルを返します。`lt` と `by` キーワードは `Base.sort` と同様に機能します。`swapsort` は最大 64 の引数をサポートします。詳細は [`tuplesort`](@ref) を参照してください。
