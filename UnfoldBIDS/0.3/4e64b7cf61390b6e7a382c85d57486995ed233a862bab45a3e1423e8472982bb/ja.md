```
load_bids_eeg_data(layout_df; verbose::Bool=true, kwargs...)
```

[`bids_layout`](@ref) で見つかったデータをメモリにロードします。

  * `verbose::Bool = true`  プログレスバーを表示
  * `kwargs...`  .tsvファイルからイベントをロードするためのCSV.readのためのkwargs; 例: デリミタを指定するため
