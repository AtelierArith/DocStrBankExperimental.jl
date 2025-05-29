```
dazldr(x, y, z; azccw=true, elplsz=true)
```

直交座標から方位/仰角座標への変換のヤコビ行列を計算します。

### 引数

  * `x`: 点のX座標
  * `y`: 点のY座標
  * `z`: 点のZ座標

### キーワード引数

  * `azccw`: 方位がどのように測定されるかを示すフラグ。`true`（デフォルト）の場合、方位は反時計回りに増加します。それ以外の場合は時計回りに増加します。
  * `elplsz`: 仰角がどのように測定されるかを示すフラグ。`true`（デフォルト）の場合、仰角はXY平面から+Zの方向に増加します。それ以外の場合は-Zの方向に増加します。

### 出力

偏微分の行列を返します。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/dazldr_c.html)

```
