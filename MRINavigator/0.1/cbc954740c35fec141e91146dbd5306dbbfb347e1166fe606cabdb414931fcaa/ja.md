```
runNavPipeline(params::Dict{Symbol, Any})
```

ナビゲーター パイプラインを実行します。再構成された画像とナビゲーター補正出力を返します (NavCorr! を確認してください)。

# 引数

  * `params::Dict{Symbol, Any}` - MRINavigator パラメータ構造体。詳細は defaultNavParams() を確認してください。
