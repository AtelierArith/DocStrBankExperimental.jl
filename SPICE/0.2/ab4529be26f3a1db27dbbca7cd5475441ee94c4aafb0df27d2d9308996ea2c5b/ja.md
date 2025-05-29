```
recazl(rectan; azccw=true, elplsz=true)
```

点の直交座標を範囲、方位角および仰角に変換します。

### 引数

  * `rectan`: 点の直交座標

### キーワード引数

  * `azccw`: 方位角の測定方法を示すフラグ。`true`（デフォルト）の場合、方位角は反時計回りに増加します。それ以外の場合は時計回りに増加します。
  * `elplsz`: 仰角の測定方法を示すフラグ。`true`（デフォルト）の場合、仰角はXY平面から+Zの方向に増加します。それ以外の場合は-Zの方向に増加します。

### 出力

次の要素からなるタプルを返します：

  * `range`: 原点からの点の距離
  * `az`: ラジアン単位の方位角
  * `el`: ラジアン単位の仰角

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/recazl_c.html)
