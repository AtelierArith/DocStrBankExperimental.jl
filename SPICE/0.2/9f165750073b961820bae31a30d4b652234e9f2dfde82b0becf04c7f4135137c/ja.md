```
drdazl(range, az, el; azccw=true, elplsz=true)
```

方位角/仰角から直交座標への変換のヤコビ行列を計算します。

### 引数

  * `range`: 原点からの点の距離
  * `az`: ラジアン単位の入力点の方位角
  * `el`: ラジアン単位の入力点の仰角

### キーワード引数

  * `azccw`: 方位角の測定方法を示すフラグ。`true`（デフォルト）の場合、方位角は反時計回りに増加します。それ以外の場合は時計回りに増加します。
  * `elplsz`: 仰角の測定方法を示すフラグ。`true`（デフォルト）の場合、仰角はXY平面から+Z方向に増加します。それ以外の場合は-Z方向に増加します。

### 出力

偏微分の行列を返します。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/drdazl_c.html)

```
