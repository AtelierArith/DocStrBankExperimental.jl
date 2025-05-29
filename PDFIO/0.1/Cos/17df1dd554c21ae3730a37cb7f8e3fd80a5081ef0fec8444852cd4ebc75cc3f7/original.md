```
    cosDocGetObject(doc::CosDoc, dict::CosObject, key::Union{CosName, CosNullType}) -> CosObject
```

Returns the object referenced inside the `dict` dictionary.

  * `dict` can be a PDF dictionary object reference or an indirect object or  a direct `CosDict` object.
  * `key` can be `CosNull` as well. In such a case, a replicated `CosDict` with  direct or indirect objects will be returned for all the input `dict`  keys.

# Example

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
