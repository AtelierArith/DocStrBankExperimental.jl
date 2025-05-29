```
export_parameters!(container, model; include_links=true)
export_parameters!(container, parameters; include_links=true)
```

指定された `container` にすべてのパラメータを書き込みます。パラメータは `name => value` ペアとして `push!` されます。リンクおよびエイリアスパラメータについては、現在の値のみが保存され、リンク情報は保存されません。リンクおよびエイリアスパラメータの書き込みを抑制するには、`include_links=false` を設定してください。

ここで作成されたコンテナからパラメータ値を復元するには [`assign_parameters!`](@ref) を使用してください。
