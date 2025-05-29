```
update_relative_signal!(batch::Batch; signal = batch.method.signal)
```

Calculate relative signal using `getproperty(batch.data, signal)` as signal data, update and insert the value into `batch.data` at index `rel_sig`, and return the updated `batch`.
