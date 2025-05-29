```
convert_to_time_series(df::DataFrame)
```

`load_data_file`を介して読み込まれた`DataFrame`を、特定のELEMENT（変数タイプ、例：降水量、温度など）に対して1か月分のデータを含む各行から、単一のELEMENTタイプに対して1日分のデータを含む各行に変換します。新しい`DataFrame`には、`df`に既に存在する要素タイプのみが含まれます。
