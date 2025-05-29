```
illumf(method, target, ilusrc, et, fixref, abcorr, obsrvr, spoint)
```

指定されたターゲットボディの点での照明角度 - 位相、入射、放出 - を計算します。観測者の位置から表面点が見えるかどうか、また表面点が照明されているかどうかを示す論理フラグを返します。

ターゲットボディの表面は、DSKファイルによって提供される地形データ、または基準楕円体を使用して表現されます。

照明源は指定された軌道要素オブジェクトです。

### 引数

  * `method`: 計算方法
  * `target`: ターゲットボディの名前
  * `ilusrc`: 照明源の名前
  * `et`: J2000 TDBからのTDB秒単位のエポック
  * `fixref`: ボディ固定、ボディ中心のターゲットボディフレーム
  * `abcorr`: 異常補正フラグ
  * `obsrvr`: 観測ボディの名前
  * `spoint`: ターゲット表面点のボディ固定座標

### 出力

  * `trgepc`: ターゲット表面点のエポック
  * `srfvec`: 観測者からターゲット表面点へのベクトル
  * `phase`: 表面点での位相角
  * `incdnc`: 表面点での源の入射角
  * `emissn`: 表面点での放出角
  * `visibl`: 可視性フラグ（可視の場合は`true`）
  * `lit`: 照明フラグ（照明されている場合は`true`）

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/illumf_c.html)
