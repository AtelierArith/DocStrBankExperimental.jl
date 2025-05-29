```
resample(transient::TransientStepData, num_datapoints, time_function)
```

データを `time_function` の間隔で再サンプリングし、隣接するデータポイント間で線形補間を行います。膨大なデータがあり、できるだけ貴重な情報を失わずにデータをスリム化する必要がある場合にこのメソッドを使用します。

# 引数

  * `transient::TransientStepData`: 再サンプリングに使用される TransientStepData
  * `num_datapoints::Integer`: 結果の TransientStepData に含まれる再サンプリングされたデータポイントの数（現在持っている数より常に少なくする必要があります）
  * `time_function::Symbol`: 時間データの重み付け方法...

      * `:Linear` は t=0 から t=num_datapoints まで均等な間隔を持ちます
      * `:Root` は時間の根に沿ってサンプリングします（初期の挙動に関するより多くの情報が保持されます）

          * ほとんどのシナリオでは :Root を使用し、迅速なシナリオでは :Linear を使用するのが通常最適です
      * `:Log` は時間の log_10 に沿ってサンプリングします（初期の挙動に関するより多くの情報が保持されます）

          * Log は非常に長い時間スケール（*月*や*年*のオーダーを考えてください、*日*や*週*ではなく）に予約してください

この関数は、時間データが昇順にソートされていることを前提としています。
