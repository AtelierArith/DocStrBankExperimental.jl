```
backup_reliability(d::Dict, p::REoptInputs, r::Dict)
```

バックアップ信頼性結果の辞書を返します。

# 引数

  * `d::Dict`: REopt 結果辞書。
  * `p::REoptInputs`: REopt 入力構造体。
  * `r::Dict`: 信頼性計算のための入力辞書。rが含まれていない場合は、すべてのデフォルトを使用します。

rの可能なキー:     -generator*operational*availability::Real = 0.995       メンテナンスのために停止していない発電機の年間割合     -generator*failure*to*start::Real = 0.0094              停電時に発電機が始動する確率     -generator*mean*time*to*failure::Real = 1100            発電機の故障間の平均時間ステップ数。 1/(運転失敗確率)。      -num*generators::Int = 1                                発電機の数。     -generator*size*kw::Real = 0.0                          バックアップ発電機の容量。      -num*battery*bins::Int = バッテリーサイズに依存      バッテリーの充電状態を離散的にモデル化するためのビンの数     -battery*operational*availability::Real = 0.97          停電開始時にバッテリーが利用可能である可能性            -pv*operational*availability::Real = 0.98               停電開始時にPVが利用可能である可能性     -wind*operational*availability::Real = 0.97             停電開始時に風力が利用可能である可能性     -max*outage*duration::Int = 96                          モデル化された最大停電期間     -microgrid_only::Bool = false                           島モード中の発電機、PV、およびバッテリーの動作を決定します ```
