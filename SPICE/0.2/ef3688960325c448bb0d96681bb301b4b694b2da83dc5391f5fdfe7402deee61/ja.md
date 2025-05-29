```
npedln(a, b, c, linept, linedr)
```

指定された直線に対する三軸楕円体上の最近点と、楕円体から直線までの距離を求めます。

### 引数

  * `a`: x方向の半軸の長さ
  * `b`: y方向の半軸の長さ
  * `c`: z方向の半軸の長さ
  * `linept`: 直線上の点
  * `linedr`: 直線の方向ベクトル

### 出力

`pnear`と`dist`からなるタプルを返します。

  * `pnear`: 直線に対する楕円体上の最近点
  * `dist`: 直線からの楕円体の距離

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/npedln_c.html)
