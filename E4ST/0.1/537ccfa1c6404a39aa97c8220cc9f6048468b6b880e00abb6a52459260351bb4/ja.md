```
modify_results!(mod::Storage, config, data)
```

バッテリーの結果を修正します。 `storage` テーブルに次の列を追加します：

  * `pcap` - ストレージデバイスの放電容量（MW単位）。
  * `pcharge` - 充電率（MW単位）
  * `pdischarge` - 放電率（MW単位）
  * `echarge` - 各代表時間に充電されたエネルギー（損失を含む）
  * `edischarge` - ストレージデバイスによって放電されたエネルギー
  * `ploss` - バッテリーによって失われた電力、`pcharge * (1-η)` として計算された供給負荷
  * `eloss` - バッテリーによって失われたエネルギー、供給負荷として計算
  * `pcap_inv_sim` - シミュレーションに投資された放電容量
  * `ecap_inv_sim` - 8760 * pcap*inv*sim

また、[`save_updated_storage_table`](@ref)を介して更新されたストレージテーブルを保存します。
