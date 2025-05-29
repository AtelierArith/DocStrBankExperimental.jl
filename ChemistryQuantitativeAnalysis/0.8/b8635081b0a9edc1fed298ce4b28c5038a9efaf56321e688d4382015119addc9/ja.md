```
set_accuracy!(at::AnalysisTable, method::AnalysisMethod; true_conc = method.true_conc, est_conc = method.est_conc, acc = method.acc)
set_accuracy!(at::AnalysisTable, batch::Batch; true_conc = batch.method.true_conc, est_conc = batch.method.est_conc, acc = batch.method.acc)
```

精度を計算し、`at`のインデックス`acc`に値を更新または挿入し、`getproperty(at, true_conc)`を真の濃度として、`getproperty(at, est_conc)`を推定濃度として使用してオブジェクトを返します。
