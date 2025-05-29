```
update_nobs!(nobs::NobsMatrixElement{T}; threshold = 1e-7)
```

この関数は、`nobs`内のすべての要素が同期されていることを確認します。これは、フィールド`nobs.m`（KurkiSuonio2009の式10の行列M_p）が変更されたときに呼び出す必要があります。
