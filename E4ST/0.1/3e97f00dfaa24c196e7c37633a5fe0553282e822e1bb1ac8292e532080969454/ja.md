```
join_sim_tables(post_mod_data, keep_col)
```

`post_mod_data`に格納された複数のシミュレーションのテーブルを結合し、`keep_col`を保持する列として、残りの列を結合列として使用します。

  * `replace_missing` - テーブルが結合された後、res内の欠損値をkw引数の値で置き換えます。欠損値を保持するには、replace_missing = missingに設定します。
