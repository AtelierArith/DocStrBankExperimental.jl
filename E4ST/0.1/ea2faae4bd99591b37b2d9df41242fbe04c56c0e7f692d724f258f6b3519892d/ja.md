```
add_build_constraints!(data, model, table_name, pcap_name)
```

モデルに対して制約を追加します：

  * `cons_<pcap_name>_prebuild` - 開始/建設年の前に容量を0に制約
  * `cons_<pcap_name>_noadd` - 既存の容量を減少させるのみ（容量を追加せずに退役のみ）
  * `cons_<pcap_name>_exog` - 未建設の外生的発電機を、year_onの翌年にpcap0に建設するように制約
  * `cons_<pcap_name>_match_min_build` - 同じサイトの発電機の最小容量が合計して>=最小容量になるように制約。
  * `cons_<pcap_name>_match_min_build` - 同じサイトの発電機の最小容量が合計して<=最大容量になるように制約。
