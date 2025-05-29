```
pytable(src, format=:pandas; ...)
```

Tables.jl互換のテーブル`src`からPythonテーブルを構築します。

`format`は結果のテーブルのタイプを制御し、次のいずれかです：

  * `:pandas`: `pandas.DataFrame`。キーワード引数は`DataFrame`コンストラクタに渡されます。
  * `:columns`: 列名を列にマッピングする`dict`。
  * `:rows`: `namedtuple`の行の`list`。
  * `:rowdicts`: `dict`の行の`list`。
