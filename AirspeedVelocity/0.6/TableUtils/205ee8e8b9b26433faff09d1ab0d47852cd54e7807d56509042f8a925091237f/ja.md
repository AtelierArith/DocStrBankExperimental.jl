```
create_table(combined_results::OrderedDict; kws...)
```

`load_results` 関数から読み込まれた結果のマークダウンテーブルを作成します。特定のベンチマークに対して2つの結果がある場合、最初のリビジョンを比較対象とする追加の列が追加されます。

`formatter` キーワード引数は列の値を生成します。デフォルトでは `TableUtils.format_time` が使用され、中央値の時間 ± 四分位範囲が表示されます。`TableUtils.format_memory` も利用可能で、割り当ての数と割り当てられたメモリを表示します。
