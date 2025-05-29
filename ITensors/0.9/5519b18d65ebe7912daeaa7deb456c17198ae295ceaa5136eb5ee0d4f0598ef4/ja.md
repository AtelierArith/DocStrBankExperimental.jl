```
not(inds::Union{IndexSet, Tuple{Vararg{Index}}})
not(inds::Index...)
!(inds::Union{IndexSet, Tuple{Vararg{Index}}})
!(inds::Index...)
```

指定された IndexSet に含まれないインデックスの集合を表し、パターンマッチング（すなわち、インデックスを検索したり、指定されたインデックスをプライミング/タグ付けしたりする際）で使用します。
