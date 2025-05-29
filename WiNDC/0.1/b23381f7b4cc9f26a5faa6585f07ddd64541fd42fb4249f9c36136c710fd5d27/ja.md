```
load_table(
    file_path::String
    years::Int...;
)
```

ファイルから `WiNDCtable` をロードします。

## 必要な引数

  * `file_path::String`: ファイルへのパス。
  * `years::Int...`: ロードする年。年が提供されない場合、ファイル内のすべての年がロードされます。

## 戻り値

ファイルからロードされたデータとセットを持つ WiNDCtable のサブタイプ。
