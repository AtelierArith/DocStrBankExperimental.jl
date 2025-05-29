```
set!(fts::OnDiskFieldTimeSeries, field::Field, n::Int, time=fts.times[time_index])
```

`parent(field)`のデータを`fts.path`のファイルに、`fts.name`の下で、`time_index`で保存します。保存されるフィールドは`time`に割り当てられ、提供されていない場合は`fts.times[time_index]`から抽出されます。
