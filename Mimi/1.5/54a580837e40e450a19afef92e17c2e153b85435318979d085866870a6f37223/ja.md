```
delete_param!(md::ModelDef, model_param_name::Symbol)
```

`model_param_name`を`md`のモデルパラメータのリストから削除し、さらに`model_param_name`に接続されていたすべての外部パラメータ接続も削除します。
