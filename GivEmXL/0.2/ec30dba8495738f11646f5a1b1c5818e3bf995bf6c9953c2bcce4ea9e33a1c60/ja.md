```
get_data(;dialogtype, filterlist="", datadir=nothing) 
    → (; abort::Bool, datafiles)
```

関数 `NativeFileDialog:` `pick_file(datadir; filterlist)` または `pick_multi_file(datadir; filterlist)` を呼び出します。 `datadir` が提供されていない場合、キャッシュされた値を使用します。選択されたディレクトリをキャッシュします。ファイルまたはフォルダまたは複数のファイルを返します。

# キーワード引数

  * `dialogtype`: dialogtype ∈ [:single, :multiple, :folder]
  * `datadir`: ファイル選択ダイアログのベースディレクトリ。
  * `filterlist`: `pick_file` / `pick_multi_file` 関数に渡されます。

# 例外

  * `dialogtype` の未知の値の場合

関数 `get_data` は公開されており、エクスポートされていません。
