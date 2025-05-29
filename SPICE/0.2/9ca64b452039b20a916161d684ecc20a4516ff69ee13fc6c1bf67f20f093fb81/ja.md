```
termpt(method, ilusrc, target, et, fixref, abcorr, corloc, obsrvr, refvec, rolstp,
       ncuts, schstp, soltol, maxn)
```

ターゲットボディ上の終端点を見つけます。呼び出し元は、終端点を検索するための照明源中心-ターゲット中心ベクトルによって境界付けられた半平面を指定します。

終端は、影の終端または半影の終端のいずれかです。影の終端は、ターゲット表面上で光源からの光が見えない領域の境界です。半影の終端は、ターゲット自体によって光源からの光が遮られないターゲット表面上の領域の境界です。

ターゲットボディの表面は、三軸楕円体または地形データによって表現される場合があります。

### 引数

  * `method`: 計算方法
  * `ilusrc`: 照明源
  * `target`: ターゲットボディの名前
  * `et`: J2000 TDBを過ぎたエポックのエフェメリス秒
  * `fixref`: ボディ固定、ボディ中心のターゲットボディフレーム
  * `abcorr`: 収差補正
  * `corloc`: 収差補正の位置
  * `obsrvr`: 観測ボディの名前
  * `refvec`: 半平面を切るための基準ベクトル
  * `rolstp`: 半平面を切るためのロール角度ステップ
  * `ncuts`: 切断平面の数
  * `schstp`: 検索のための角度ステップサイズ
  * `soltol`: 解の収束許容範囲
  * `maxn`: 出力配列の最大エントリ数

### 出力

  * `npts`: 切断に対応する終端点のカウント
  * `points`: 終端点
  * `epochs`: 終端点に関連する時間
  * `trmvcs`: 観測者から放出される終端ベクトル

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/termpt_c.html)
