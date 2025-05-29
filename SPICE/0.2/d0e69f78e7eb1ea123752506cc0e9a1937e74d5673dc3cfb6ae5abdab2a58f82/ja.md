```
latsrf(method, target, et, fixref, npts, lonlat)
```

指定されたターゲット天体の表面点に惑星中心の経度/緯度座標ペアの配列をマップします。

ターゲット天体の表面は、三軸楕円体またはDSKファイルによって提供される地形データで表される場合があります。

### 引数

  * `method`: 計算方法
  * `target`: ターゲット天体の名前
  * `et`: J2000 TDBからのTDB秒単位のエポック
  * `fixref`: 天体固定、天体中心のターゲット天体フレーム
  * `lonlat`: 経度/緯度座標ペアの配列

### 出力

表面点の配列を返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/latsrf_c.html)
