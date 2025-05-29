```
    pdDocGetCatalog(doc::PDDoc) -> CosObject
```

`Catalog` は、PDF ドキュメント内で最上位のオブジェクトと見なされ、その後、PDF ドキュメントから情報をトラバースし抽出するために使用されます。直接的な API が利用できない場合に、ドキュメント構造から PDF 内部オブジェクトにアクセスするために使用されます。

# 例

```
julia> pdDocGetCatalog(doc)

154 0 obj
<<
	/Pages	152 0 R
	/Type	/Catalog
>>
endobj
```
