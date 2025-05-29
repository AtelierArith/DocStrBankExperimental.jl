```
srfnrm(method, target, et, fixref, npts, srfpts)
```

指定されたターゲットボディ上の表面点の配列を対応する単位長の外向き表面法線ベクトルにマップします。

ターゲットボディの表面は、三軸楕円体またはDSKファイルによって提供される地形データで表される場合があります。

### 引数

  * `method`: 計算方法
  * `target`: ターゲットボディの名前
  * `et`: J2000 TDBからのTDB秒単位のエポック
  * `fixref`: ボディ固定、ボディ中心のターゲットボディフレーム
  * `srfpts`: 表面点の配列

### 出力

外向きの単位長法線ベクトルの配列を返します。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/srfnrm_c.html)
