```
class_group(O::AbsSimpleNumFieldOrder; bound = -1,
                      redo = false,
                      GRH = true)   -> FinGenAbGroup, Map
```

$$
A
$$

と$O$のイデアルの集合への写像$f$を返します。写像の逆は、主イデアルの群を除いたイデアルの群への射影です。

デフォルトでは、正確性は一般化リーマン予想（GRH）を仮定した場合にのみ保証されます。

キーワード引数:

  * `redo`: 再計算をトリガーし、キャッシュを回避します。
  * `bound`: 指定された場合、これは因子基のための境界として使用されます。
  * `GRH`: `false`の場合、結果の正確性はGRHに依存しません。
