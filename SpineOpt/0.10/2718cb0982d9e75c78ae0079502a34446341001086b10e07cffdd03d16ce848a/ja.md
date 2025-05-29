```
write_report_from_intermediate_results(intermediate_results_folder, default_url; <keyword arguments>)
```

以前の失敗したSpineOpt実行から`intermediate_results_folder`に生成された結果を収集し、対応するレポートを`url_out`に書き込みます。`url_out`にデータベースが存在しない場合は、新しいSpineデータベースが作成されます。

# 引数

  * `alternative::String=""`: 空でない場合、出力DBの指定された代替に結果を書き込みます。
  * `log_level::Int=3`: ログレベルを制御する整数。
