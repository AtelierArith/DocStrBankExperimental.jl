```
parse_power_results!(config, data, res_raw)
```

電力ベースの結果を追加します。以下の要約については、[`get_table_summary`](@ref)も参照してください。

| table_name | col_name      | unit                       | description                                                        |
|:---------- |:------------- |:-------------------------- |:------------------------------------------------------------------ |
| :bus       | :pgen         | MWGenerated                | このバスで生成された平均電力                                                     |
| :bus       | :pflow        | MWFlow                     | このバスから流出する平均電力                                                     |
| :bus       | :pflow_in     | MWFlow                     | このバスに流入する平均電力                                                      |
| :bus       | :pflow_out    | MWFlow                     | このバスに流入する平均電力                                                      |
| :bus       | :plserv       | MWServed                   | このバスで供給される平均電力                                                     |
| :bus       | :plcurt       | MWCurtailed                | このバスでカーテイルされた平均電力                                                  |
| :gen       | :pgen         | MWGenerated                | この発電機で生成された平均電力                                                    |
| :gen       | :pcap         | MWCapacity                 | この発電機の発電能力、重み付けされた代表時間における発電能力                                     |
| :gen       | :ecap         | MWhCapacity                | この発電機の総エネルギー生成能力、重み付けされた代表時間における発電能力                               |
| :gen       | :pcap_retired | MWCapacity                 | 各年に引退した発電能力                                                        |
| :gen       | :pcap_built   | MWCapacity                 | 各年に建設された発電能力                                                       |
| :gen       | :pcap*inv*sim | MWCapacity                 | シミュレーション中にこの発電機に投資された総発電能力。（単一値）。引退後も同じ                            |
| :gen       | :ecap*inv*sim | MWhCapacity                | シミュレーション中にこの発電機に投資された年間発電エネルギー能力。（pcap*inv*sim * 年間時間）（単一値）。引退後も同じ |
| :gen       | :cf           | MWhGeneratedPerMWhCapacity | キャパシティファクター、または平均発電/発電能力、発電がない場合は0                                 |
| :branch    | :pflow        | MWFlow                     | ブランチを通過する平均電力                                                      |
| :branch    | :eflow        | MWFlow                     | 代表時間におけるブランチを通過する総エネルギー                                            |
