```
vv = rk_vvsat(T,a,b)
```

レドリッヒ-クワン cubic 状態方程式の飽和蒸気体積を返します。

入力:

  * `T`: 温度 (ケルビン)
  * `a`: 引力パラメータ `[m^6*Pa/mol]`
  * `b`: コボリューム `[m^3/mol]`

出力:

  * `vv` : 飽和蒸気体積 `[m^3]`。値が補助の範囲外の場合は `NaN` を返します。
