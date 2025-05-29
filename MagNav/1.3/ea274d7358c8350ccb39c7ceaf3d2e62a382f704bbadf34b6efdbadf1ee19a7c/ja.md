```
get_comp_params(comp_params_bson::String, silent::Bool = false)
```

保存されたBSONファイルから空中磁気補償パラメータを取得します。

**引数:**

  * `comp_params_bson`: 空中磁気補償パラメータBSONファイルのパス/名前（`.bson`拡張子はオプション）
  * `silent`:           （オプション）trueの場合、出力は行われません

**戻り値:**

  * `comp_params`: `CompParams` 空中磁気補償パラメータ構造体、次のいずれか：

      * `NNCompParams`:  ニューラルネットワークベースの空中磁気補償パラメータ構造体
      * `LinCompParams`: 線形空中磁気補償パラメータ構造体
