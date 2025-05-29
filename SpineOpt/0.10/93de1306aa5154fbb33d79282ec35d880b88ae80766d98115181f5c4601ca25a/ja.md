```
run_spineopt!(m, url_out; <キーワード引数>)
```

与えられた `m` で SpineOpt を構築し、解決します。報告書を `url_out` に書き込みます。`url_out` に Spine データベースが存在しない場合は、新しいデータベースが作成されます。

# 引数

  * `log_level`
  * `optimize`
  * `update_names`
  * `alternative`
  * `write_as_roll`
  * `log_file_path`
  * `resume_file_path`

キーワード引数の説明については [run_spineopt](@ref) を参照してください。
