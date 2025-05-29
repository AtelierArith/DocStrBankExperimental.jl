```julia
add_to_dataframe!(df, stats)
add_to_dataframe!(df, stats, pre)
add_to_dataframe!(df, stats, pre, post)

```

観察タイプ `stats_t` の結果をデータフレーム `df` に格納します。`pre` と `post` を使用することで、stats オブジェクトに含まれていない追加データを追加できます。
