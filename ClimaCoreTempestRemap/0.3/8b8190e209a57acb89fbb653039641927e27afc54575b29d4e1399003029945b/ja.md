```
write_exodus(filename, topology::Topology2D; normalize_coordinates=true)
```

トポロジーをExodus形式のNetCDFファイルに書き込みます。

Exodus II仕様に従うように試みますが、主にTempestRemapでの使用を目的としています。

注意: 生成されるメッシュは、TempestRemap自体によって生成されるノードと要素の順序とは異なるものになります。

この関数をMPIの分散トポロジー入力で使用する場合は、単一のプロセスでのみ呼び出す必要があります。

オプション:

  * `normalize_coordinates`: trueの場合、座標は単位球上に正規化されます（これはTempestRemapでの使用に必要です）

# 参考文献

  * EXODUS II: A finite element data model: https://www.osti.gov/biblio/10102115-exodus-ii-finite-element-data-model

```
