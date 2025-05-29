```
save_all_plots(overview, subsets_results, résumé, rslt_dir, paramsets) → nothing
```

生成されたプロットオブジェクトを指定された形式のファイルに保存します。

# 引数

  * `overview`, `subsets_results`, `résumé`::NamedTuple: 実際のデータ処理の結果を (; plots=(;df1, df2...), ...) の形式で表したもの。キー 'plots' はオプションです。
  * `rslt_dir`: ファイルを置くディレクトリ。
  * `paramsets::Vector{NamedTuple}`: paramsets[1] にフィールド `plotformat` がある場合、それがプロットを保存するための形式になります。

関数 `save_all_plots` は公開されており、エクスポートされていません。
