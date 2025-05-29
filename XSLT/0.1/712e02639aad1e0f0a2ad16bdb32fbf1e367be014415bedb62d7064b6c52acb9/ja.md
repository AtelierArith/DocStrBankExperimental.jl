```
read_xml(file)
```

XMLファイル`file`を読み込み、`xsltPtr`（`xmlDocPtr`に相当）を返します。

この関数はXMLファイルを解析せず、単に読み込んでポインタに格納し、XSLTパッケージでのさらなる使用のために準備します。XMLファイルを解析したい場合は、EzXML.jlまたはLightXML.jlの関数を使用してください。

# 例

```julia
using XSLT

# パッケージ内のテストファイルからXMLファイルを取得します:
file = joinpath(dirname(pathof(XSLT)), "..", "test", "files", "cd_catalog.xml")

# XMLファイルを読み込みます:
xml = read_xml(file)
```
