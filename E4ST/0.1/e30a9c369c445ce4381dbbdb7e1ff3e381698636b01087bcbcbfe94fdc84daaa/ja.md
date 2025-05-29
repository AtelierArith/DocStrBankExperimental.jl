```
match_capacity!(data, model, table_name::Symbol, pcap_name::Symbol, name::Symbol, sets::Vector{Vector{Int64}})
```

`sets` の発電機インデックスを制約し、それらの `pcap_gen` 値がセットの最初のメンバーで指定された最大値と最小値の合計になるようにします。制約の名前は次のとおりです：

  * `Symbol("cons_pcap_max_$name")`
  * `Symbol("cons_pcap_min_$name")`
