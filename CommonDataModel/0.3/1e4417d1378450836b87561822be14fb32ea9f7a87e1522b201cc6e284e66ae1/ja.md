```
Base.setindex!(a::Attributes,data,name::SymbolOrString)
```

属性リスト `a` において、`name` という名前の属性を `data` の値に設定します。`data` はベクトルまたはスカラーであることができます。スカラーは、NetCDF データモデルでは要素が1つのベクトルとして扱われます。

一般的に、属性はインデクシングによって定義されます。例えば：

```julia
ds = NCDataset("file.nc","c")
ds.attrib["title"] = "my title"
close(ds)
```
