```
update_inv_predict!(batch::Batch; rel_sig = batch.method.rel_sig, est_conc = batch.method.est_conc)
```

相対信号データとして `getproperty(batch.data, rel_sig)` または `dt` を使用して濃度を逆に予測し、値を `batch.data` のインデックス `est_conc` に更新または挿入し、更新された `batch` を返します。
