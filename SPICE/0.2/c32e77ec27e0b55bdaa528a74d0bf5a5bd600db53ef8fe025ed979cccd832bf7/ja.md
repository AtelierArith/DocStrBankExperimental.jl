```
subpnt(method, target, et, fixref, obsrvr, abcorr)
```

指定されたエポックでターゲット天体のサブオブザーバーポイントの直交座標を計算します。光時間および星の収差の補正をオプションで行うことができます。

### 引数

  * `method`: 計算方法
  * `target`: ターゲット天体の名前
  * `et`: J2000 TDBからのエポメリス秒でのエポック
  * `fixref`: 天体固定、天体中心のターゲット天体フレーム
  * `abcorr`: 収差補正
  * `obsrvr`: 観測天体の名前

### 出力

  * `spoint`: ターゲット天体のサブソーラーポイント
  * `trgepc`: サブソーラーポイントのエポック
  * `srfvec`: 観測者からサブソーラーポイントへのベクトル

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/subpnt_c.html)
