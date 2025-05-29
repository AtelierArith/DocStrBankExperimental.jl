```
download_if_needed(url::String, output::String, sha256sum::String)
```

`url`から`output`にファイルをダウンロードします。ファイルがすでに存在しない場合、またはそのSHA256チェックサムが`sha256sum`と一致しない場合に限ります。

# 引数

  * `url::String`: ファイルをダウンロードするためのURL。
  * `output::String`: ダウンロードされたファイルが保存されるパス。

# キーワード引数

  * `sha256sum::String`: ファイルの整合性を確保するために期待されるSHA256チェックサム。

# 出力

  * `nothing`: この関数は`nothing`を返します。ファイルをダウンロードし、そのチェックサムを検証する副作用を実行します。チェックサムが一致しない場合、関数はエラーを発生させ、ダウンロードされたファイルを削除します。

*クレジット: Átila Saraiva Quintela Soares, 2024*
