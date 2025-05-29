```
vv = ref_vvsat(fluid::REFPROPSuperanc, T)
```

参照流体 `fluid` の温度 `T` における飽和蒸気体積を返します。

入力:

  * `fluid`: 参照流体（`REFPROPSuperAnc` のインスタンス）
  * `T`: 温度（ケルビン）

出力:

  * `vv` : 飽和蒸気体積 `[m^3]`。値が補助範囲外の場合は `NaN` を返します。
