```
PBSystem(grid;
             celldata=ElectrolyteData(),
         bcondition=(f, u, n, e)-> nothing,
         kwargs...)
```

VoronoiFVMシステムを一般化したポアソン-ボルツマンを作成します。入力:

  * `grid`: 離散化グリッド
  * `celldata`: 電解質データを含む複合構造体
  * `bcondition`: 境界条件
  * `kwargs`: VoronoiFVM.Systemのキーワード引数
