```
chebpoints(order, lb, ub)
```

与えられた `order`（多項式の次数の配列またはタプル）およびハイパーキューブの下限および上限ベクトル `lb` と `ub` に対して、チェビシェフ点（`SVector` 値として）を返します。 `ub` と `lb` が数値の場合、数値の配列を返します。

これらは、`chebinterp` を使用してチェビシェフ補間を作成するために関数を評価すべき点です。

（各次元に沿った点の数は、その方向の次数に `1 +` です。）
