```
read_stylesheet(filename::String)
```

スタイルシート `filename` を読み込み、`xsltPtr`（`xsltStylesheetPtr` に相当）を返します。スタイルシートは、[`xml_xslt`](@ref) を使用して XML ドキュメントに適用できます。

# 例

```julia
using XSLT

# パッケージ内のテストファイルからスタイルシートを取得します：
file = joinpath(dirname(pathof(XSLT)), "..", "test", "files", "cd_catalog.xsl")

# スタイルシートを読み込みます：
xslt = read_stylesheet(file)
```
