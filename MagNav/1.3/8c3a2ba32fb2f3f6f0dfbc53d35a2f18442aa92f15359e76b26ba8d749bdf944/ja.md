```
save_comp_params(comp_params::CompParams,
                 comp_params_bson::String = "comp_params.bson")
```

BSONファイルに航空磁気補償パラメータを保存します。

**引数:**

  * `comp_params`: `CompParams` 航空磁気補償パラメータ構造体、いずれか:

      * `NNCompParams`: ニューラルネットワークベースの航空磁気補償パラメータ構造体
      * `LinCompParams`: 線形航空磁気補償パラメータ構造体
  * `comp_params_bson`: (オプション) 保存する航空磁気補償パラメータBSONファイルのパス/名前（`.bson`拡張子はオプション）

**戻り値:**

  * `nothing`: `comp_params_bson` が作成されます
