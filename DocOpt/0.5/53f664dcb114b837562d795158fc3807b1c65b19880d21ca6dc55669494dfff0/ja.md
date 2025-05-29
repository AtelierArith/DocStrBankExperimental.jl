```
docopt(doc::AbstractString,
       args=ARGS;
       version=nothing,
       help::Bool=true,
       options_first::Bool=false,
       exit_on_error::Bool=true)
```

コマンドライン引数をヘルプメッセージに従って解析します。

解析されたコマンドライン引数は、引数の型 `Dict{AbstractString,Any}` の辞書として返されます。キーは引数名またはフラグ名であり、値はコマンドライン引数に渡された引数の値です。

ヘルプの説明言語については http://docopt.org/ を参照してください。

# 引数

  * `doc`: コマンドラインインターフェースの説明。
  * `args=ARGS`: 解析される引数ベクター。
  * `version=nothing`: コマンドラインツールのバージョン（例: `v"1.0.2"`）。
  * `help=true`: '-h' または '–help' が渡されたときにヘルプを表示します。
  * `options_first=false`: オプションが位置引数の前に来るように強制します。
  * `exit_on_error=true`: 解析エラーが発生したときに使用法を印刷して終了します。
