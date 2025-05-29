```
Highs_passLinearObjectives(highs, num_linear_objective, weight, offset, coefficients, abs_tolerance, rel_tolerance, priority)
```

HiGHSに複数の線形目的データを渡し、HiGHSに既に存在するデータをクリアします。

### パラメータ

  * `highs`: Highsインスタンスへのポインタ。
  * `weight`: 線形目的の重みへのポインタ。正負の符号によって、辞書式最適化中に最小化されるか最大化されるかが決まります。
  * `offset`: 目的のオフセットへのポインタ。
  * `coefficients`: 目的の係数へのポインタ。
  * `abs_tolerance`: 辞書式最適化中に目的制約を構築する際に使用される絶対許容誤差へのポインタ。
  * `rel_tolerance`: 辞書式最適化中に目的制約を構築する際に使用される相対許容誤差へのポインタ。
  * `priority`: 辞書式最適化中の目的の優先度へのポインタ。

### 戻り値

呼び出しが成功したかどうかを示す`kHighsStatus`定数。
