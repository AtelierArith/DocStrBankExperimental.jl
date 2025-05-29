```
eachoverlap(intervals_a, intervals_b, [groupname_isless=Base.isless])
```

`intervals_a` と `intervals_b` の間の重複する区間のイテレータを作成します。

この関数は、`intervals_a` と `intervals_b` の要素がグループ名と左位置でソートされていることを前提としています。要素の型が `GenomicFeatures.AbstractGenomicInterval` のサブタイプでない場合、要素は `GenomicInterval` オブジェクトに変換されます。

第三のオプション引数は、グループ名の順序を定義する関数です。デフォルトの関数は `Base.isless` で、これは辞書式順序です。
