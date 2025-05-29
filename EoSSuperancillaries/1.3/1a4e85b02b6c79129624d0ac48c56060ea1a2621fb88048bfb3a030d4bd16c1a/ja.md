```
vl = ref_vlsat(fluid::REFPROPSuperanc, T)
```

参照流体 `fluid` の温度 `T` における飽和液体体積を返します。

入力:

  * `fluid`: 参照流体（`REFPROPSuperAnc` のインスタンス）
  * `T`: 温度（ケルビン）

出力:

  * `vl` : 飽和液体体積 `[m^3]`。値が補助範囲外の場合は `NaN` を返します。
