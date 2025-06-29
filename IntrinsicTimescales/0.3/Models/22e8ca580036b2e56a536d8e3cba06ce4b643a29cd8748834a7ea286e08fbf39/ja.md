```
fit(model::AbstractTimescaleModel, param_dict=nothing)
```

指定されたフィッティング方法を使用してタイムスケールモデルをフィットします。

# 引数

  * `model`: フィットするタイムスケールモデルのインスタンス
  * `param_dict`: オプションのフィッティングパラメータの辞書。提供されない場合、デフォルトのパラメータが使用されます。

# 戻り値

ADVIフィッティング方法の場合：

  * `samples`: 事後サンプルの配列
  * `map_estimate`: パラメータの最大事後推定
  * `vi_result`: 完全な変分推論結果オブジェクト

ABCフィッティング方法の場合：

  * `samples`: 受け入れられたパラメータサンプルの配列
  * `weights`: サンプルの重要度重み
  * `distances`: シミュレーションされた要約統計量と観測された要約統計量の間の距離
