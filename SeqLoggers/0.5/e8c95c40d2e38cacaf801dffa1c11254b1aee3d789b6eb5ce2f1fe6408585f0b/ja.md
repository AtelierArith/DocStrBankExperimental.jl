```
AdvancedFileLogger(
    dir::AbstractString, 
    file_name_pattern::AbstractString;
    log_format_function::Function=print_standard_format,
    min_level=Logging.Info
)
```

追加機能を持つファイルロガーを返します（`SimpleLogger`へのインターフェースである`FileLogger`とは対照的です）。

### パラメータ

  * `dir` – ログファイルディレクトリ
  * `file_name_pattern` – ログファイルを回転させるためのファイル名パターン（例: `raw"\a\c\c\e\s\s-YYYY-mm-dd-HH-MM.\l\o\g"`）
  * `log_format_function` – オプション、デフォルト=`print_standard_format`
  * `min_level` – オプション、デフォルト=`Logging.Info`

### 特徴

  * ログメッセージを新しいファイルに回転させるための`DateFormat`/`String`ファイルパターンを定義する → 引数`file_name_pattern`
  * ログファイルに書き込むためのカスタムフォーマット関数を提供する → 引数`log_format_function`

### 戻り値

`DatetimeRotatingFileLogger`を含む`MinLevelLogger`。
