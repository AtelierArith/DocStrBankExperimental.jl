```
dtwplot(seq1, seq2, [dist=SqEuclidean()]; transportcost=1, diagonal=false)
dtwplot(seq1, seq2, D, i1, i2; transportcost=1, diagonal=false)
dtwplot(seq1, seq2, D; transportcost=1, diagonal=false)
```

2つのシーケンスが与えられた場合、動的時間ワーピングを実行し、結果をプロットします。アライメントがすでに計算されている場合は、プロットを作成するためにインデックス `i1` と `i2` を渡します。

`diagonal = true` は視覚的な補助として対角線マーカーをプロットします。
