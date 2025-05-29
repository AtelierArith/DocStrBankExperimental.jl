```
getInterpolationWeightsBatch(tsg, llfX):
```

は、getPoints()内のポイントに関連付けられた補間重みを返します。

単一のライブラリ呼び出しで複数の重みを見つけ、libtasmaniansparsegrids.soでOpenMPが有効になっている場合は使用します。

x: 最初の次元がgetNumDimensions()の行列    配列内の各列は単一の要求されたポイントです。

出力: 行列         次元はgetNumPoints() X size(llfX, 2)           各行はllfXの1行に対する重みに対応します。
