```
show_params(io::IO, pip::ParameterIndexingProxy; num_rows = 20, show_all = false, scalarize = true, kwargs...)
```

テーブル出力をカスタマイズするためのメソッド。キーワード引数:

  * num_rows
  * show*all: すべてのパラメータを表示するかどうか。`num*rows`を上書きします。
  * scalarize: テーブル出力で配列のシンボリックをスカラー化するかどうか。
  * kwargs... は pretty_table 呼び出しに渡されます。
