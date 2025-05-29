```
update_relative_signal!(batch::Batch; signal = batch.method.signal)
```

相対信号を計算するには、`getproperty(batch.data, signal)`を信号データとして使用し、`batch.data`のインデックス`rel_sig`に値を更新して挿入し、更新された`batch`を返します。
