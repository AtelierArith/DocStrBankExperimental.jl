DCパワーフローの結果を含む辞書を返します。各キーは考慮された時間期間の名前に対応し、PF結果を含むDataFrameを格納します。

# 引数:

  * `data::Union{PTDFPowerFlowData, vPTDFPowerFlowData, ABAPowerFlowData}`:       電力フローとバス角度を含むPowerFlowData構造体。
  * `sys::PSY.System`:       システム情報を格納するコンテナ。
