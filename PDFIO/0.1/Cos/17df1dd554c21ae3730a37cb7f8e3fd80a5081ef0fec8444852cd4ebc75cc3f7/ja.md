```
    cosDocGetObject(doc::CosDoc, dict::CosObject, key::Union{CosName, CosNullType}) -> CosObject
```

`dict` 辞書内で参照されているオブジェクトを返します。

  * `dict` は PDF 辞書オブジェクトの参照、間接オブジェクト、または直接の `CosDict` オブジェクトであることができます。
  * `key` は `CosNull` であることも可能です。その場合、すべての入力 `dict` キーに対して、直接または間接オブジェクトを持つ複製された `CosDict` が返されます。

# 例

```
julia> catalog

652 0 obj
<<
	/Outlines	555 0 R
	/PageLayout	/SinglePage
	/PageMode	/UseOutlines
	/Pages	446 0 R
	/Type	/Catalog
	/OpenAction	[447 0 R /XYZ null null 0 ]
>>
endobj

julia> pages = cosDocGetObject(doc.cosDoc, catalog, cn"Pages")

446 0 obj
<<
	/Kids	[447 0 R 449 0 R 451 0 R]
	/Count	3
	/Type	/Pages
>>
endobj

julia> cosDocGetObject(doc.cosDoc, catalog, cn"PageLayout")
/SinglePage
```
