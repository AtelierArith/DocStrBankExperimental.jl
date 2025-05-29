```
limbpt(method, target, et, fixref, abcorr, corloc, obsrvr, refvec, rolstp, ncuts, schstp,
       soltol, maxn)
```

ターゲットボディのリムポイントを見つけます。リムは、観測者から放射される光線の接点の集合です。呼び出し元は、リムポイントを検索するための観測者-ターゲット中心ベクトルによって制限された半平面を指定します。

ターゲットボディの表面は、三軸楕円体または地形データによって表現される場合があります。

### 引数

  * `method`: 計算方法
  * `target`: ターゲットボディの名前
  * `et`: J2000 TDBを過ぎたエポックのエフェメリス秒
  * `fixref`: ボディ固定、ボディ中心のターゲットボディフレーム
  * `abcorr`: 収差補正
  * `corloc`: 収差補正の位置
  * `obsrvr`: 観測ボディの名前
  * `refvec`: 半平面を切るための基準ベクトル
  * `rolstp`: 半平面を切るためのロール角度ステップ
  * `ncuts`: 切断半平面の数
  * `schstp`: 検索のための角度ステップサイズ
  * `soltol`: 解の収束許容範囲
  * `maxn`: 出力配列の最大エントリ数

### 出力

タプル `(npts, points, epochs, tangts)` を返します。

  * `npts`: カットに対応するリムポイントのカウント
  * `points`: リムポイント
  * `epochs`: リムポイントに関連する時間
  * `tangts`: 観測者から放射される接線ベクトル

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/lgrind_c.html)
