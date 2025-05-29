```
dskx02(handle, dladsc, vertex, raydir)
```

指定されたレイとタイプ2 DSKプレートモデルによって定義された表面との交差点のプレートIDとボディ固定座標を決定します。

### 引数

  * `handle`: プレートモデルを含むDSKカーネルのハンドル
  * `dladsc`: プレートモデルセグメントのDLA記述子
  * `vertex`: ボディ固定フレーム内のレイの頂点
  * `raydir`: ボディ固定フレーム内のレイの方向

### 出力

交差点が存在しない場合は`nothing`を返すか、または

  * `plid`: レイと交差したプレートのIDコード
  * `xpt`: 交差点

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/dskx02_c.html)
