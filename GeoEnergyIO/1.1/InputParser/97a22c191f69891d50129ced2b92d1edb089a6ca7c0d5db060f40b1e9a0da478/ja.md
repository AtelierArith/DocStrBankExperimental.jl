```
region = get_data_file_cell_region(data, t::Symbol; active = nothing)
satnum = get_data_file_cell_region(data, :satnum)
pvtnum = get_data_file_cell_region(data, :pvtnum, active = 1:10)
```

`data`に格納されたドメインの各セルのタイプの領域インジケーターを取得します（[`parse_data_file`](@ref)からの出力）。オプションのキーワード引数`active`を使用して、セルのサブセットの値を抽出できます。

`t`は次のいずれかである必要があります：

  * `:satnum`（飽和関数領域）
  * `:pvtnum`（PVT関数領域）
  * `:eqlnum`（平衡領域）
  * `:eosnum`（状態方程式領域）
