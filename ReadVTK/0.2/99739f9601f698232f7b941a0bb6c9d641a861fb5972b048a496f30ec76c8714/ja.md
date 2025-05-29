```
get_example_file(filename; head="main", output_directory=".", force=false)
```

[`ReadVTK_examples` リポジトリ](https://github.com/JuliaVTK/ReadVTK_examples) からコミット/ブランチ `head` の例ファイルを取得し、`output_directory` に保存します。ファイルがすでにローカルに存在する場合、`force` が true でない限り、再度ファイルをダウンロードしません。ダウンロードしたファイルのローカルパスを返します。
