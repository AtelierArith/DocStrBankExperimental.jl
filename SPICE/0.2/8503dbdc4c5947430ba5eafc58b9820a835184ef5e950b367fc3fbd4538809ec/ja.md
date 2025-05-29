```
bodvcd(bodyid, item)
```

カーネルプールから、整数IDコードで指定された天体に関連付けられた項目の倍精度値を取得します。

### 引数

  * `bodyid`: 天体IDコード
  * `item`: 値が必要な項目。(`"RADII"`, `"NUT_PREC_ANGLES"`, など)
  * `maxn`: 返される可能性のある最大値の数（デフォルト: 100）

### 出力

要求された値を返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/bodvcd_c.html)
