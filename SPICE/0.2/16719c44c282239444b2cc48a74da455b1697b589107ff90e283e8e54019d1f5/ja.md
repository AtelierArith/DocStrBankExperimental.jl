```
subslr(method, target, et, fixref, abcorr, obsrvr)
```

指定された時刻におけるターゲット天体の太陽点の直交座標を計算します。光時間および星の収差の補正をオプションで行うことができます。

### 引数

  * `method`: 計算方法
  * `target`: ターゲット天体の名前
  * `et`: J2000 TDBからのエフェメリス秒での時刻
  * `fixref`: 天体固定、天体中心のターゲット天体フレーム
  * `abcorr`: 収差補正
  * `obsrvr`: 観測天体の名前

### 出力

  * `spoint`: ターゲット天体の太陽点
  * `trgepc`: 太陽点の時刻
  * `srfvec`: 観測者から太陽点へのベクトル

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/subslr_c.html)
