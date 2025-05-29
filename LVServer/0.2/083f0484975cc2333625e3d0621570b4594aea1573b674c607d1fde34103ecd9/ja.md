```
get_script_path(p)
```

ユーザー定義関数を含むJuliaスクリプトをフルパスで受け取るか、このパッケージに付属する例のファイル名を受け取ります。ファイルが見つからない場合は、空のファイル "dummy.jl" へのパスを返します。`p` が空文字列の場合は、いくつかの例のスクリプトを含む "Examples-UserFn.jl" へのパスを返します。すべてが正常であれば、グローバル変数 `scriptexists` を `true` に設定します。

# 例

```julia-repl

julia> include(get_script_path(raw"C:\Users\eben\Desktop\Julia\my_functions.jl"))
julia> server_0mq4lv((;foo=foo, bar, baz))
```
