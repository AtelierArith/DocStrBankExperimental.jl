```
collate_files(file_contents::AbstractVector{<:AbstractDict})
```

ファイルの内容を単一の文字列にまとめます。

# 引数

  * `file_contents::AbstractVector{<:AbstractDict}`: リポジトリ内のファイルの内容。`:name` と `:content` フィールドが必要です。

# 戻り値

  * `String`: 連結されたファイル名と内容を含む文字列。
