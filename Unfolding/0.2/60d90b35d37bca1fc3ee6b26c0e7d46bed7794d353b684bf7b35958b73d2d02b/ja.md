```
errors(mode, coords, unf_coords; search=:knn, neigh=16, maxerr=5)
```

展開は隣接点間の元の距離を歪めます。この関数は `mode` に応じて2種類の結果を返します。

`mode = :ids` の場合、これは `maxerr` 閾値を超えた点のIDをタプルとして返します。タプルは (テストに合格した ids, テストに合格しなかった ids) です。

`mode = :dists` の場合、この関数は近傍で分析された各ペアの期待される距離の差を出力します。歪みを検証するためにボックスプロットの入力として使用できます。

## パラメータ:

  * `mode`       - エラーのタイプ、:ids または :dists。
  * `coords`     - 展開前の点の座標行列。
  * `unf_coords` - 展開後の点の座標行列。
  * `search`     - 近傍のタイプ、:knn または :radius。
  * `neigh`      - 検証に使用される隣接点の数または半径。
  * `maxerr`     - mode = :ids の場合に許容される距離の最大絶対差。
