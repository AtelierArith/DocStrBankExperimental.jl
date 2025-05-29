```
read_xl_paramtables(f_src; paramtables=(;setup="params_setup", exper="params_experiment")) 
    → (; df_setup::Union{Nothing, DataFrame}, df_exp::Union{Nothing, DataFrame})
```

XLSXファイルから2つのテーブル（`nothing`でない場合）を対応するDataFrameに読み込み、コメントがあればそれを削除します。コメントは`#`で始まる行です。

# 引数

  * `f_src::String`: ファイルパス

# キーワード引数

  * `paramtables=(;setup::Union{Nothing, String}="params_setup", exper::Union{Nothing, String}="params_experiment")`

# 返されるNamedTuple

  * `(;df_setup::Union{Nothing, DataFrame}, df_exp::Union{Nothing, DataFrame}`

関数`read_xl_paramtables`はエクスポートされています。
