```
folder_path(folder::Vector, root, foldertype)
```

フォルダのリストのフルパスを返し、存在しない場合はオプションでパスを作成します。

# 引数

  * `folders`: フォルダ名のリスト。
  * `root`: ルートディレクトリ。
  * `foldertype`: フォルダのタイプ（オプション、デフォルトは空文字列）。
  * `make`: 存在しない場合にパスを作成するかどうかを示すブールフラグ（オプション、デフォルトは `false`）。

# 返り値

  * `Vector{String}`: 指定されたフォルダのフルパス。
