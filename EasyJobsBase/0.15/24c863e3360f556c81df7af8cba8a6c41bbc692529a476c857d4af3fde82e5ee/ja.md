```
timecostof(job::AbstractJob)
```

`job`が実行を開始してからの時間コストを返します。

`nothing`の場合、`job`はまだ保留中です。完了している場合は、完了するのにかかった時間を返します。
