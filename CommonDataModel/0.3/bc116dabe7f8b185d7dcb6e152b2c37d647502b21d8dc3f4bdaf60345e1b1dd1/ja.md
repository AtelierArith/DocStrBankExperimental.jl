```
getindex(a::Attributes,name::SymbolOrString)
```

属性リスト `a` から `name` と呼ばれる属性の値を返します。一般的に、属性はインデックスを使用してロードされます。例えば：

```julia
using NCDatasets
ds = NCDataset("file.nc")
title = ds.attrib["title"]
```
