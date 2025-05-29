```
D = stats(D::GMTdataset, cols=0) -> GMTdataset
```

データセット `GMTdataset` の記述統計を返します。各行は各列の統計を表します。

`cols` が列名（文字列またはシンボル）または列番号の場合、その列の統計のみが返されます。
