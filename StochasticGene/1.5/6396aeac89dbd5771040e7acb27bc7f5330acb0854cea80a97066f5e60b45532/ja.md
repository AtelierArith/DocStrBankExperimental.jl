```
folder_path(folder::String, root::String, folderatetype::String=""; make=false)
```

指定されたフォルダーのフルパスを返し、存在しない場合はオプションでパスを作成します。

# 引数

  * `folder`: フォルダー名。
  * `root`: ルートディレクトリ。
  * `foldertype`: フォルダーのタイプ（オプション、デフォルトは空の文字列）。
  * `make`: 存在しない場合にパスを作成するかどうかを示すブールフラグ（オプション、デフォルトは `false`）。

# 戻り値

  * `String`: 指定されたフォルダーのフルパス。
