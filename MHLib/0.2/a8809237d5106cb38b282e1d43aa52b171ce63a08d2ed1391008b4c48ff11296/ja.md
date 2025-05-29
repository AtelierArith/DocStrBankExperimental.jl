```
remove_some!(::SubsetVectorSolution, k)
```

解決策からランダムに選択された `min(k,sel)` 要素を削除します。

`element_removed_delta_eval` を使用し、問題に合わせてオーバーロードおよび適応する必要があります。解決策が不適切になっても要素は削除されます。
