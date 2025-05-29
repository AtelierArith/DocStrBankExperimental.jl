```
set_inv_predict(at::AnalysisTable, batch::Batch; rel_sig = batch.method.rel_sig, est_conc = batch.method.est_conc)
```

相対信号データとして `getproperty(at, rel_sig)` を使用して濃度を逆に予測し、`at` のコピーのインデックス `est_conc` に値を更新または挿入し、そのコピーを返します。
