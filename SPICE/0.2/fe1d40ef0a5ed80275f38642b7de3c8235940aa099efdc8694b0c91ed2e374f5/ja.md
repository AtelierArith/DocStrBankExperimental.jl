```
azlrec(range, az, el; azccw=true, elplsz=true)
```

点の範囲、方位角、高度を直交座標に変換します。

### 引数

  * `range`: 原点からの点までの距離
  * `az`: ラジアンでの方位角
  * `el`: ラジアンでの高度

### キーワード引数

  * `azccw`: 方位角の測定方法を示すフラグ。`true`（デフォルト）の場合、方位角は反時計回りに増加します。それ以外の場合は時計回りに増加します。
  * `elplsz`: 高度の測定方法を示すフラグ。`true`（デフォルト）の場合、高度はXY平面から+Zの方向に増加します。それ以外の場合は-Zの方向に増加します。

### 出力

  * `rectan`: 点の直交座標

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/azlrec_c.html)
