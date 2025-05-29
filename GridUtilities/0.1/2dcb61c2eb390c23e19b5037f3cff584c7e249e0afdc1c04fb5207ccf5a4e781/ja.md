```
StorePlan(sample_time,varlist[;htype=RegularHistory,min_time=-Inf,max_time=Inf])
```

履歴データを保存するためのプランを作成します。データの保存は、`sample_time`で指定されたサンプル間隔で行われることが指定されています。オプションとして、サンプリングウィンドウの初期時間`min_time`と最終時間`max_time`（含む）を指定することもできます。これらはデフォルトで全ての時間になります。保存する変数のリストは、カンマ区切りの名前付きペアとして提供される変数のリスト`varlist`として指定されます。例えば、`"varname1"-> v1,"varname2"-> v2`のようになります。オプションの引数`htype`は、履歴データを`PeriodicHistory`または`RegularHistory`（デフォルト）に設定するために使用できます。`PeriodicHistory`の場合、データは`length(history)+1`に等しい周期で繰り返されると仮定されます。
