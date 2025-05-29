```
saveplots(rs, rslt_dir; plotformat = "png", kwargs...) → nothing
```

生成されたプロットオブジェクトを指定された形式のファイルに保存します。

# 引数

  * `rs`: 処理結果を含むNamedTuple。
  * `rslt_dir`: ファイルを保存するディレクトリ。

# キーワード引数

  * `plotformat = "png"`: plotformat == "none" の場合、保存しません。
  * その他のkwargsは無視されます。

関数 `saveplots` は公開されており、エクスポートされていません。
