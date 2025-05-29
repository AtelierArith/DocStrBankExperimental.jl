```
UnderwaterEnvironment(; kwargs...)
```

与えられたパラメータを使用して一般的な水中環境を作成します。サポートされているパラメータは次のとおりです。

  * `bathymetry` = 水深モデル
  * `altimetry` = 高度モデル
  * `temperature` = 温度モデル
  * `salinity` = 塩分モデル
  * `soundspeed` = 音速プロファイルモデル
  * `density` = 密度モデル
  * `seabed` = 海底堆積物モデル
  * `surface` = 表面モデル

すべてのパラメータはオプションであり、デフォルト値があります。環境内の対応するプロパティを設定することで、構築後にパラメータを変更できます。
