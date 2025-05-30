```
 select(y::EventSeries, t1, t2)
```

は、入力系列のサブセットであるEventSeriesを返し、時間領域[tstart, tend]内の`Event`を含みます。エンドポイントの値は前方補完によって設定されます。入力時間領域[t1, t2]が入力EventSeriesに含まれていると仮定します。
