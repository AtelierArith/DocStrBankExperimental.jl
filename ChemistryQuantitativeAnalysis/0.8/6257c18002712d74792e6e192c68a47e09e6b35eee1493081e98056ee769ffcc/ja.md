```
update_accuracy!(batch::Batch; true_conc = batch.method.true_conc, est_conc = batch.method.est_conc, acc = batch.method.acc)
```

精度を計算し、`batch.data` または `batch.data` のコピーに `acc` インデックスで値を更新または挿入し、更新された `batch` を返します。`getproperty(batch.data, true_conc)` を真の濃度として、`getproperty(batch.data, est_conc)` を推定濃度として使用します。この関数は `at` を `batch.data` に割り当てます。
