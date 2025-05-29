```
set_inv_predict!(at::AnalysisTable, batch::Batch; rel_sig = batch.method.rel_sig, est_conc = batch.method.est_conc)
```

相対信号データとして `getproperty(at, rel_sig)` を使用して濃度を逆に予測し、値を `at` のインデックス `est_conc` に更新または挿入し、`at` を返します。
