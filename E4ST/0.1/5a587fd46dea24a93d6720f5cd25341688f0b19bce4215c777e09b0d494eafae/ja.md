```
iterate!(iter::RunSequential, config, data) -> nothing
```

次のように反復します：

  * 設定の年を増加させる
  * `config[:out_path]`を`"iter<n>"`に変更する
  * `config[:gen_file]`を変更する
