```
build_config(data_dir::String, config_file::String)
```

インタラクティブにユーザーをガイドして、DeIdentificationのための設定YAMLファイルを作成します。`data_dir`には、デアイデンティファイすることを期待する各タイプのデータセットが1つずつ含まれている必要があります（例：データディレクトリ`./test/data'`には`pat.csv`、`med.csv`、および`dx.csv`が含まれています）。設定ビルダーは各CSVファイルのヘッダーを読み取り、各列の出力名とデアイデンティフィケーションタイプについて逐次的に質問します。結果は`config_file`に書き込まれます。
