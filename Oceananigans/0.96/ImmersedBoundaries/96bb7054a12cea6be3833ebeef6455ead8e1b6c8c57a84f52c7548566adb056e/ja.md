```
GridFittedBottom(bottom_height, [immersed_condition=CenterImmersedCondition()])
```

底面が浸漬された境界を返します。

# キーワード引数

  * `bottom_height`: 底面の高さを絶対$z$座標で与える配列または関数。
  * `immersed_condition`: 浸漬された領域の一部が、`bottom_height`の下にあるすべてのセル中心であるか                       (`CenterImmersedCondition()`; デフォルト)                       または`bottom_height`の下にあるすべてのセル面であるか                       (`InterfaceImmersedCondition()`)を決定します。                       `immersed_condition`の唯一の目的は、                       `GridFittedBottom`と`PartialCellBottom`が、                       部分セルの最小分数セル高さが0に設定されているときに                       同じ動作をすることを可能にすることです。
