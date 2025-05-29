```
merge(sc1, sc2...)
```

これは、SortedDictまたはSortedMultiDictを返します。これは、すべて同じキー-値-順序タイプを持つSortedDictまたはSortedMultiDict `sc1`、`sc2`などをマージした結果です。引数の間でキーが重複している場合、キーを所有する最も右側の引数の値がSortedDictに保存されます。SortedMultiDictの場合、すべてのキー-値ペアが保存され、`sc1`と`sc2`の間で共有されるキーについては、順序が左から右になります。この関数はSortedSetには利用できませんが、`union`関数（下記参照）が同等の機能を提供します。時間: O(*cN* log *N*)、ここで*N*はすべての引数の合計サイズです。
