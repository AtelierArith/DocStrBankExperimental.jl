```
p = ref_psat(fluid::REFPROPSuperanc, T)
```

参照流体 `fluid` の温度 `T` における飽和圧力を返します。

入力:

  * `fluid`: 参照流体（`REFPROPSuperAnc` のインスタンス）
  * `T`: 温度（ケルビン）

出力:

  * `p` : 飽和圧力 `[Pa]`。値が補助範囲外の場合は `NaN` を返します。
