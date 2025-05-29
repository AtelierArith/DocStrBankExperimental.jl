```
getdx_err(date; outside_range=:warn)
```

特定の `date` に対する天体極 x 座標補正の誤差をミリ秒で取得します。

`date` は `DateTime` オブジェクトまたは数値で表されたユリウス日であることができます。`outside_range` 引数は、`date` に対してデータが利用できない場合に何をするかを決定します：

  * `:warn`: 最後の有効な値が返され、警告が表示されます。
  * `:nothing`: 最後の有効な値が返されます。
  * `:error`: `OutOfRangeError` がスローされます。
