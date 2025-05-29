```
export_parameters(model; include_links=true)
export_parameters(parameters; include_links=true)
```

すべてのパラメータを `Dict{Symbol, Any}` に書き込みます。リンクおよびエイリアスパラメータについては、現在の値のみが保存され、リンク情報は保存されません。リンクおよびエイリアスパラメータの書き込みを抑制するには、`include_links=false` を設定してください。

[`assign_parameters!`](@ref) を使用して、ここで作成されたコンテナからパラメータ値を復元します。
