```
sincpt(method, target, et, fixref, abcorr, obsrvr, dref, dvec)
```

観測者と光線を定義する方向ベクトルが与えられたとき、指定されたエポックでのターゲット天体上の光線の表面交点を計算します。光時間と星の収差の補正をオプションで行うことができます。

ターゲット天体の表面は、三軸楕円体またはDSKファイルによって提供される地形データで表現できます。

### 引数

  * `method`: 計算方法
  * `target`: ターゲット天体の名前
  * `et`: J2000 TDBからのTDB秒単位のエポック
  * `fixref`: 天体固定、天体中心のターゲット天体フレーム
  * `abcorr`: 収差補正フラグ
  * `obsrvr`: 観測天体の名前
  * `dref`: 光線の方向ベクトルの基準フレーム
  * `dvec`: 光線の方向ベクトル

### 出力

次のデータからなるタプルを返します。交点が見つからなかった場合は`nothing`を返します。

  * `spoint`: ターゲット天体上の表面交点
  * `trgepc`: 交点エポック
  * `srfvec`: 観測者から交点までのベクトル

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/sincpt_c.html)

```
