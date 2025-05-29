```
build_config_from_csv(project_name::String, file::String)
```

CSVファイルからマッピングを定義する構成YAMLファイルを生成します。CSVファイルには、データが読み込まれるCSVファイルの名前を定義する**Source Table**という名前の列、データソース内のフィールドの名前を定義する**Field**という名前の列、適用するメソッドを含む**Method**という名前の列の少なくとも3つの名前付き列が必要です（**Hash - Research ID**、**Hash**、**Hash & Salt**、**Date Shift**、または**Drop**のいずれか）。

列の名前変更や前処理・後処理は、ファイルに手動で追加する必要があります。
