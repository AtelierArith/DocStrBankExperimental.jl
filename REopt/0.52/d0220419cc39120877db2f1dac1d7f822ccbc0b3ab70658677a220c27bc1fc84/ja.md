```
backup_reliability(r::Dict)
```

バックアップ信頼性結果の辞書を返します。

# 引数

  * `r::Dict`: 信頼性計算のための入力の辞書。rが含まれていない場合はすべてのデフォルトを使用します。

rの可能なキー: -critical*loads*kw::Array                               時間ステップごとの重要負荷。（必須入力） -microgrid*only::Bool                                   グリッド停電中にマイクログリッドのみが稼働するかどうかを確認するブール値（デフォルトはfalse） -chp*size*kw::Real                                      CHP容量。  -pv*size*kw::Real                                       PVシステムのサイズ -pv*production*factor*series::Array                     時間ステップごとのPV生産係数（辞書にpv*size*kwが含まれている場合は必須） -pv*migrogrid*upgraded::Bool                            trueの場合、microgrid*only = TRUEのときにPVが停電中に稼働します（デフォルトはfalse） -battery*size*kw::Real                                  バッテリー容量。バッテリーが設置されていない場合、PVは停電中にシステムから切断されます -battery*size*kwh::Real                                 バッテリーエネルギー貯蔵容量 -battery*charge*efficiency::Real                        バッテリー充電効率 -battery*discharge*efficiency::Real                     バッテリー放電効率 -battery*starting*soc*series*fraction::Array            通常のグリッド接続使用中のバッテリーの充電状態のパーセント時系列 -generator*failure*to*start::Real = 0.0094              停電時に発電機が始動する確率 -generator*mean*time*to*failure::Real = 1100            発電機の故障間の平均時間ステップ数。（運転失敗確率の逆数） -num*generators::Int = 1                                発電機の数。 -generator*size*kw::Real = 0.0                          バックアップ発電機の容量。 -num*battery*bins::Int = num*battery*bins*default(r[:battery*size*kw],r[:battery*size*kwh])     バッテリーの充電状態を離散的にモデル化するためのビンの数 -max*outage*duration::Int = 96                          モデル化された最大停電期間
