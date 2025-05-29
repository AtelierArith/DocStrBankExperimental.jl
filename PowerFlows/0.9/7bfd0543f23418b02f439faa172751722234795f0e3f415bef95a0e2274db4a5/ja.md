各システムのブランチにおける電力フローを仮想PTDF行列を用いて評価します。PowerFlowData構造体「data」を更新し、「data」で考慮されたタイムステップの数と同じ数のDataFrameを含む辞書を返します。DataFrameには、入力として考慮されたPSY.Systemに保存された情報に関連するフローと角度が含まれています。

# 引数:

  * `::vPTDFDCPowerFlow`:       仮想PTDF行列に基づく方法に従って電力フローを評価するためにvPTDFDCPowerFlow()を使用します
  * `sys::PSY.System`:       フローと角度の評価に使用されるシステムデータを集約するコンテナです。
