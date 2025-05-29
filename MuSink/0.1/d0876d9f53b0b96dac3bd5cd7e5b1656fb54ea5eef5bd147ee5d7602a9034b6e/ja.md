```
marginal(ws::Workspace, node; keep_batchdim = false)
```

カウント測度に関する`node`での周辺測度。

`keep_batchdim = true`の場合、バッチサイズが1の場合の特異なバッチ次元は削除されません。
