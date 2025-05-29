```
t8_forest_element_points_inside(forest, ltreeid, element, points, num_points, is_inside, tolerance)
```

要素内にバッチのポイントがあるかどうかを照会します。バイリニア補間された要素の場合。

!!! note
    2D四角形要素の場合、この関数は近似値です。4つの頂点が同じ平面にある場合は正しいですが、頂点が同じ平面にない場合は近似的な結果しか得られない可能性があります。


# 引数

  * `forest`:[in] 森。
  * `ltree_id`:[in] 要素がある木の森のローカルID。
  * `element`:[in] 要素。
  * `points`:[in] 確認するポイントの3次元座標
  * `num_points`:[in] 確認するポイントの数
  * `is_inside`:[in,out] 長さ*num_points*の配列で、出力時に0/1で埋められます。*point*が*element*内にある場合は真（非ゼロ）、そうでない場合は偽。ポイントが要素の境界上にある場合も戻り値は真になります。したがって、この関数は異なる葉要素に対して真を返す場合があります。隣接していて、ポイントが共通の境界上にある場合です。
  * `tolerance`:[in] ポイントが要素と正確に一致しないことを許可する許容誤差。この値が大きいほど、より多くのポイントを検出します。ゼロの場合、丸め誤差のために内部にあってもポイントを検出できない可能性があります。

### プロトタイプ

```c
void t8_forest_element_points_inside (t8_forest_t forest, t8_locidx_t ltreeid, const t8_element_t *element, const double *points, int num_points, int *is_inside, const double tolerance);
```
