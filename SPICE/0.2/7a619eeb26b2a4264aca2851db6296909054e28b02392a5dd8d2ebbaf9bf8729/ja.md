```
eqncpv(et, epoch, eqel, rapol, decpol)
```

オブジェクトの状態（位置と速度）を計算します。このオブジェクトの軌道は、いくつかの固定平面（通常は惑星の赤道平面）に対する等分点要素によって記述されます。

### 引数

  * `et`: J2000からの経過秒数でのエポック
  * `epoch`: J2000からの経過秒数での要素のエポック
  * `eqel`: 等分点要素の配列
  * `rapol`: 参照平面の極の赤経
  * `decpol`: 参照平面の極の赤緯

### 出力

`eqel`によって記述されたオブジェクトの状態を返します。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/eqncpv_c.html)
