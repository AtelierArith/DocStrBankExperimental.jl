```
depgraph_web(pkgname, base_url = first(webapps); kw...)
```

`pkgname`の依存関係グラフの画像をブラウザで開きます。

`base_url`の詳細については[`url`](@ref)を参照してください。キーワード引数は[`depgraph_as_dotstr`](@ref)に渡されます。
