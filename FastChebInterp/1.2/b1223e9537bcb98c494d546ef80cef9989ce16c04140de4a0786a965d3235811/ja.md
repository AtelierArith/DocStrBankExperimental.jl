```
chebinterp(vals, lb, ub; tol=eps)
```

与えられた多次元配列 `vals` は、`chebpoints` によって返される座標に対応する点での関数値を含み、配列 `lb` と `ub` は各方向の領域の下限および上限の座標境界を示します。この関数は、チェビシェフ補間オブジェクト（`ChebPoly`）を返します。

このオブジェクト `c = chebinterp(vals, lb, ub)` は、点 `x` で補間多項式を評価するために `c(x)` を介して使用できます。

`vals` の要素は、ベクトル値の関数を補間するために、数値だけでなくベクトルでもあり得ます（つまり、複数の関数を同時に補間することができます）。

`tol` 引数は、チェビシェフ係数が削除される相対的な許容誤差を指定します。これは `float(vals)` の精度に対してマシン精度にデフォルト設定されています。`tol=0` を渡すと、`chebpoints` に渡された次数までのすべての係数が保持されます。
