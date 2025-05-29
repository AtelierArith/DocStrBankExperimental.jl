```
nodepartitioning(fens::FENodeSet, fesarr, npartitions::Vector{Int})
```

ノードの慣性カット分割を計算します。

`fesarr` = 領域を表す有限要素セットの配列 `npartitions` = 各領域の分割数の配列。ただし、実際の分割数は2の累乗であることに注意してください。

分割自体は、分割に含めるノードのリストを使って`nodepartitioning()`によって実行されます。各領域Iについて、分割に含まれるノードは、その領域の要素に接続されているノードですが、前の領域1…I-1に属する要素には接続されていません。
