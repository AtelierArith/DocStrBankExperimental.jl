```
PNPSystem(grid;
         celldata=ElectrolyteData(),
         bcondition=(f, u, n, e)-> nothing,
         reaction=(f, u, n, e)-> nothing,
         kwargs...)
```

一般化ポアソン-ネルンスト-プランクのためのVoronoiFVMシステムを作成します。入力:

  * `grid`: 離散化グリッド
  * `celldata`: 電解質データを含む複合構造体
  * `bcondition`: 境界条件
  * `reaction` : バルク種の反応
  * `kwargs`: VoronoiFVM.Systemのキーワード引数
