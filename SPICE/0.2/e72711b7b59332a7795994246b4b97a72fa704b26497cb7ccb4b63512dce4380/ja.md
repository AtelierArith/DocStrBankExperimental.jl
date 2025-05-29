```
gfoclt(occtyp, front, fshape, fframe, back, bshape, bframe, abcorr, obsrvr, step, cnfine,
       maxwin=100)
```

観測者が一つのターゲットが別のターゲットによって隠されている、または通過しているのを見る時間間隔を決定します。

ターゲット天体の表面は、三軸楕円体またはDSKファイルによって提供される地形データで表すことができます。

### 引数

  * `occtyp`: 隠蔽のタイプ
  * `front`: 他の天体を隠す天体の名前
  * `fshape`: 前面天体に使用される形状モデルのタイプ
  * `fframe`: 前面天体のための天体固定、天体中心のフレーム
  * `back`: 他の天体によって隠される天体の名前
  * `bshape`: 背面天体に使用される形状モデルのタイプ
  * `bframe`: 背面天体のための天体固定、天体中心のフレーム
  * `abcorr`: 収差補正フラグ
  * `obsrvr`: 観測する天体の名前
  * `step`: 隠蔽イベントを見つけるためのステップサイズ（秒単位）
  * `cnfine`: 検索が制限されるウィンドウ
  * `maxwin`: 出力ウィンドウの最大サイズ（デフォルト: 100）

### 出力

結果を含むウィンドウを返します。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/gfoclt_c.html)
