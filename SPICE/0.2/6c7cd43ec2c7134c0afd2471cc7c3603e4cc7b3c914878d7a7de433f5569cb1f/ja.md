```
gfocce!(occtyp, front, fshape, fframe, back, bshape, bframe, abcorr, obsrvr, tol,
        udstep, udrefn, rpt, udrepi, udrepu, udrepf, cnfine, result)
```

観測者が一つのターゲットが別のターゲットによって隠されているのを見る時間間隔を決定します。

### 引数

  * `occtyp`: 隠蔽のタイプ
  * `front`: 他のものを隠す天体の名前
  * `fshape`: 前面天体に使用される形状モデルのタイプ
  * `fframe`: 前面天体のための天体固定、天体中心のフレーム
  * `back`: 他のものによって隠される天体の名前
  * `bshape`: 背面天体に使用される形状モデルのタイプ
  * `bframe`: 背面天体のための天体固定、天体中心のフレーム
  * `abcorr`: 収差補正フラグ
  * `obsrvr`: 観測する天体の名前
  * `tol`: 秒単位の収束許容範囲
  * `udstep`: 時間ステップを返すルーチンの名前
  * `udrefn`: 精密な時間を計算するルーチンの名前
  * `rpt`: 進捗報告フラグ
  * `udrepi`: 進捗報告を初期化する関数
  * `udrepu`: 進捗報告を更新する関数
  * `udrepf`: 進捗報告を最終化する関数
  * `cnfine`: 検索が制限されるSPICEウィンドウ
  * `result`: 結果を含むSPICEウィンドウ

### 出力

`result`を返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/gfocce_c.html)
