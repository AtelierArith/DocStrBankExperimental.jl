```
Highs_addLinearObjective(highs, weight, offset, coefficients, abs_tolerance, rel_tolerance, priority)
```

HiGHSに線形目的データを追加します

### パラメータ

  * `highs`: Highsインスタンスへのポインタ。
  * `weight`: 線形目的の重みで、正負の符号によって、辞書式最適化中に最小化されるか最大化されるかが決まります。
  * `offset`: 目的のオフセット
  * `coefficients`: 目的の係数へのポインタ
  * `abs_tolerance`: 辞書式最適化中に目的制約を構築する際に使用される絶対許容誤差
  * `rel_tolerance`: 辞書式最適化中に目的制約を構築する際に使用される相対許容誤差
  * `priority`: 辞書式最適化中のこの目的の優先度

### 戻り値

呼び出しが成功したかどうかを示す`kHighsStatus`定数。
