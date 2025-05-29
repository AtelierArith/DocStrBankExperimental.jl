```
get_xl(; basedir=nothing, paramtables = (;setup="params_setup", exper="params_experiment")) 
    → (;abort, xlargs=rslt, fname)
```

関数 `NativeFileDialog:` `pick_file(datadir; filterlist)` を呼び出してXLSXを選択します。選択したファイルを `read_xl_paramtables` に渡してパラメータテーブルを解析します。`basedir` が提供されていない場合は、キャッシュされた値を使用します。選択したディレクトリをキャッシュします。

# キーワード引数

  * `dialogtype`: dialogtype ∈ [:single, :multiple, :folder]
  * `basedir`: ファイル選択ダイアログのベースディレクトリ。

# 戻り値のNamedTuple

  * `abort::Bool`: ユーザーによってダイアログがキャンセルされた
  * `xlargs::NamedTuple`: DataFramesに読み込まれたテーブル - s. [`read_xl_paramtables`](@ref)
  * `fname::String`: 選択されたXLSXファイル

関数 `get_xl` は公開されており、エクスポートされていません。
