```
SVGJS([output::Union{IO,AbstractString}], width=√200cm, height=10cm, jsmode=:embed) -> Backend
```

Gadflyのインタラクティビティ（パン、ズームなど）を可能にするスケーラブルベクターグラフィックバックエンドを作成します。デフォルトの`jsmode`は、必要なjavascriptを出力に直接挿入します。代わりに、`:linkabs`や`:linkrel`を使用して同じ外部javascriptにリンクすることもできます。出力は通常、[`draw`](@ref)に渡されます。最初の引数として文字列を使用してファイル名を指定します。詳細は[`SVG`](@ref)を参照してください。
