```
open_db(database_name, [experiment_folder, create_folder]; in_memory=false)
```

データベースを開き、Experimenter.jlスキーマでExperiment、Trial、Snapshotのテーブルを準備します。データベースがすでに存在する場合は、それを開き、既存のデータを上書きしません。

`in_memory`を`true`に設定すると、すべての引数をスキップし、データベースを「メモリ内」に作成するため、永続化されません。
