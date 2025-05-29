```
illumg(method, target, ilusrc, et, fixref, obsrvr, spoint, abcorr)
```

指定されたターゲットボディの表面点での照明角度（位相、入射、放出）を求めます。

ターゲットボディの表面は、三軸楕円体またはDSKファイルによって提供される地形データで表現できます。

照明源は指定されたエフェメリスオブジェクトです。

### 引数

  * `method`: 計算方法。
  * `target`: ターゲットボディの名前。
  * `ilusrc`: 照明源の名前。
  * `et`: J2000 TDBからのエフェメリス秒でのエポック。
  * `fixref`: ボディ固定、ボディ中心のターゲットボディフレーム。
  * `obsrvr`: 観測ボディの名前。
  * `spoint`: ターゲット表面点のボディ固定座標。
  * `abcorr`: 異常補正。

### 出力

  * `trgepc`: サブソーラーポイントエポック。
  * `srfvec`: 観測者からサブソーラーポイントへのベクトル。
  * `phase`: 表面点での位相角。
  * `incdnc`: 表面点での太陽入射角。
  * `emissn`: 表面点での放出角。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/illumg_c.html)
