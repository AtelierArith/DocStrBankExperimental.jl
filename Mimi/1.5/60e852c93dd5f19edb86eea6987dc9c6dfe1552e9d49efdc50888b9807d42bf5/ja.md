```
delete_param!(m::Model, model_param_name::Symbol)
```

モデル `m` の ModelDef のモデルパラメータのリストから `model_param_name` を削除し、また `model_param_name` に接続されていたすべての外部パラメータ接続も削除します。
