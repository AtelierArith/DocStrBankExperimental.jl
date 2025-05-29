```
xf2eul(xform, axisa, axisb, axisc)
```

指定された軸セットに関して、状態変換行列をオイラー角とその導関数に変換します。

### 引数

  * `xform`: 状態変換行列
  * `axisa`: オイラー角の因子分解の軸A
  * `axisb`: オイラー角の因子分解の軸B
  * `axisc`: オイラー角の因子分解の軸C

### 出力

オイラー角とその導関数の配列のタプルと、これが一意の表現であるかどうかを示すブール値を返します。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/xf2eul_c.html)
