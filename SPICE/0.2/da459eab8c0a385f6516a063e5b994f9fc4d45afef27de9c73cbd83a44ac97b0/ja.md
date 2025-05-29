```
ilumin(method, target, et, fixref, obsrvr, spoint, abcorr)
```

指定されたターゲット天体の表面点での照明角度（位相、太陽入射、放出）を求めます。

### 引数

  * `method`: 計算方法
  * `target`: ターゲット天体の名前
  * `et`: J2000 TDBからのエポック（エフェメリス秒）
  * `fixref`: 天体固定、天体中心のターゲット天体フレーム
  * `obsrvr`: 観測天体の名前
  * `spoint`: ターゲット表面点の天体固定座標
  * `abcorr`: 異常補正

### 出力

  * `trgepc`: サブソーラーポイントエポック
  * `srfvec`: 観測者からサブソーラーポイントへのベクトル
  * `phase`: 表面点での位相角
  * `incdnc`: 表面点での太陽入射角
  * `emissn`: 表面点での放出角

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ilumin_c.html)
