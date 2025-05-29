```
v = variable(ds::NCDataset,varname::String)
```

データセット `ds` から NetCDF 変数 `varname` を `NCDataset.Variable` として返します。変数 `v` がインデックス付けされるとき、スケーリングやその他の変換は適用されません。
