```
parse_results!(config, data, model) -> nothing
```

  * モデルに保存されている各変数、式、および制約の値とシャドウプライスを収集し、それらを `data[:results][:raw]` にダンプします（[`get_raw_results`](@ref) および [`get_results`](@ref) を参照）。
  * `gen`、`bus`、および `branch` テーブルに関連情報を追加します。詳細については、[`parse_lmp_results!`](@ref) および [`parse_power_results!`](@ref) を参照してください。
  * 更新された `gen` テーブルを [`save_updated_gen_table`](@ref) を介して保存します。
  * `config[:save_data_parsed]` が `false` でない限り（デフォルトでは true）、`data` を `get_out_path(config,"data_parsed.jls")` に保存します。
