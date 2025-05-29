```
dsstxt_to_sparse_array(fp::String, first_data_row::Int = 5)
```

OpenDSSからのSystemY.txtファイルをjulia行列に変換します。Yが対称であると仮定します。
