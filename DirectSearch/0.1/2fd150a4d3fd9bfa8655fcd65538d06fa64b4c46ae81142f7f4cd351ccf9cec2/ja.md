```
CacheSaveJLD2(p::AbstractProblem{T}, filename::String, dataset::String="cache_costs") where T
```

キャッシュからコストをJLD2ファイルに`filename`という名前で保存し、データセット`dataset`に保存します。デフォルトのデータセットは'cache_costs'という名前です。1つのファイルに複数のデータセットに書き込むことは可能ですが、データセットを上書きすることはできません。
