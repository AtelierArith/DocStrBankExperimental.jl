```
edterm(trmtyp, source, target, et, fixref, abcorr, obsrvr, npts)
```

指定されたターゲット天体の影または半影の終端に沿った点のセットを計算します。ターゲットの形状は楕円体としてモデル化されています。

### 引数

  * `trmtyp`: 終端のタイプ
  * `source`: 光源
  * `target`: ターゲット天体
  * `et`: 観測時刻
  * `fixref`: ターゲットに関連付けられた天体固定フレーム
  * `abcorr`: 異常補正
  * `obsrvr`: 観測者
  * `npts`: 終端セット内の点の数

### 出力

  * `trgepc`: ターゲット中心に関連付けられた時刻
  * `obspos`: 天体固定フレーム内の観測者の位置
  * `trmpts`: 終端点セット

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/edterm_c.html)

```
