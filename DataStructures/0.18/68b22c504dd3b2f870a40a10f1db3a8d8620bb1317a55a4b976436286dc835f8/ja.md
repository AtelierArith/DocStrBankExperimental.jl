```
first(sc)
```

引数 `sc` は SortedDict、SortedMultiDict または SortedSet です。この関数は、コンテナ内のソートされた順序に従って最初のアイテム（SortedDict および SortedMultiDict の場合は `k=>v` ペア、SortedSet の場合はキー）を返します。したがって、`first(sc)` は `deref((sc,startof(sc)))` と同等です。この関数を空のコンテナで呼び出すことはエラーです。時間: O(log *n*)
