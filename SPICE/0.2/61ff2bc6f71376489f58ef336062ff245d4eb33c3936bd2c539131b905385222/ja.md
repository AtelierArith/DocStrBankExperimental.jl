```
azlcpo(target, et, abcorr, obspos, obsctr, obsref;
       method="ELLIPSOID", azccw=true, elplsz=true)
```

指定されたターゲットの方位/標高座標を、"観測者"に対して返します。観測者は指定された参照フレーム内で一定の位置にあります。観測者の位置は、読み込まれたSPKファイルではなく、呼び出しプログラムによって提供されます。

### 引数

  * `target`: ターゲットの軌道オブジェクトの名前
  * `et`: 観測時刻
  * `abcorr`: 収差補正
  * `obspos`: 動きの中心に対する観測者の位置
  * `obsctr`: 観測者の動きの中心
  * `obsref`: 観測者の中心の体固定、体中心フレーム

### キーワード引数

  * `method`: 表面法線ベクトルを取得する方法。現在サポートされている唯一の（およびデフォルトの）選択肢は `"ELLIPSOID"` です
  * `azccw`: 方位がどのように測定されるかを示すフラグ。`true`（デフォルト）の場合、方位は反時計回りに増加します。それ以外の場合は時計回りに増加します
  * `elplsz`: 標高がどのように測定されるかを示すフラグ。`true`（デフォルト）の場合、標高はXY平面から+Zの方向に増加します。それ以外の場合は-Zの方向に増加します

### 出力

  * `azlsta`: 観測者に対するターゲットの状態、方位/標高座標で: `azlsta = [r, az, el, dr/dt, daz/dt, del/dt]`
  * `lt`: ターゲットと観測者の間の片道光時間

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/azlcpo_c.html)

```
