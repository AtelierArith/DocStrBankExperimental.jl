```
xml_xslt(x, xslt, params= nothing)
```

与えられた `params` で XML `x` にスタイルシート `xslt` を適用します。

# 引数

  * `x`: ファイルパス、[`read_xml`](@ref) によって返されるポインタ、EzXML.jl の `Document` または LightXML.jl の `XMLDocument` であることができます。
  * `xslt`: ファイルパスまたは [`read_stylesheet`](@ref) の出力である `xsltPtr` であることができます。
  * `params`: パラメータのキーと値の辞書、タプル、または Vector{Pair} です。また、`["param1", ""stringvalue1"", "param2", "1"]` の形式の文字列のベクターを直接指定することもできます。

結果を文字列として返します。

# 例

```julia
using EzXML
using XSLT

# パッケージ内のテストファイルへのパスを取得します:
test_dir = joinpath(dirname(pathof(XSLT)), "..", "test", "files")

xml = readxml(joinpath(test_dir, "cd_catalog.xml"))
xslt = joinpath(test_dir, "cd_catalog.xsl")

res = xml_xslt(xml, xslt)

write("cd_catalog.html", res)
```
